---
layout: post
title: React⚛ Hooks-UseAxios
color: rgb(242,85,44)
tags: [websolute, team, React, Hooks, front-end, web, framework]
---

### UseAxios

axios는 HTTP 클라이언트 라이브러리로써, 비동기 방식으로 HTTP 데이터 요청을 실행한다.

```javascript
const useAxios = (opts, axiosInstance = defaultAxios) => {
  const [trigger, setTrigger] = useState(0);

  const [state, setState] = useState({
    loading: true,
    error: null,
    data: null,
  });
  useEffect(() => {
    axiosInstance(opts)
      .then((data) => {
        setState({
          ...state,
          loading: false,
          data,
        });
      })
      .catch((error) => {
        setState({ ...state, loading: false, error });
      });
  }, [trigger]);

  if (!opts.url) {
    return;
  }

  const refetch = () => {
    setState({
      ...state,
      loading: true,
    });
    setTrigger(Date.now());
  };

  return { ...state, refetch };
};

const App = () => {
  const { loading, data, error, refetch } = useAxios({
    url: "http://localhost:3004/www.naver.com",
  });
  return (
    <div className="App">
      <h1>{data && data.status}</h1>
      <h2>{loading && "Loading"}</h2>
      <button onClick={refetch}>Refetch</button>
    </div>
  );
};
```

`const useAxios = (opts, axiosInstance = defaultAxios) => {`
opts -> configuration

axiosinstance 요청 ,axios는 약간의 customization(맞춤화)과 configuration(구성)허용 만약 얻지 못했다면 import한 axios 전달한다.
