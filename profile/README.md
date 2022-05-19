# 얼로너즈(Alonerz)

```
다양한 분야의 사람들과 함께 밥을 먹으며, 전문 분야의 지식과 통찰을 얻기 위한 모임 플랫폼 서비스
```

2017년 트렌드 키워드인 `aloner`는 혼자라는 뜻의 `alone`과 명사형 접미사 `er`가 혼합된 '혼자인 삶을 즐기는 사람들'이라는 의미의 단어입니다. 저희 서비스는 사람들 간의 생산적인 모임을 제공하기 위해 '우리'를 뜻하는 `us`를 `z`로 표기하여 Alonerz로 명명하였습니다.

# Contributors

|                  백엔드                   |                프론트엔드                |                   디자이너                   |
| :---------------------------------------: | :--------------------------------------: | :------------------------------------------: |
|    [최원영](https://github.com/choewy)    |  [김형중](https://github.com/fomula91)   |    [김령은](https://behance.net/ella_re)     |
| [김지웅](https://github.com/KimJiWoong02) | [김민우](https://github.com/purplephone) | [장민선](https://blog.naver.com/alstjs11120) |

# Architecture

![alonerz-1 drawio](https://user-images.githubusercontent.com/70950533/169298516-23e6d109-606f-411a-bfef-8f0727cbf4d1.png)

# Technical Stacks

- 공통 : `Kakao Map API`, `Kakao Login API`, `JWT OAuth`, `Socket.io`, `TypeScript`
- 프론트엔드 : `React`, `Redux`, `Styled-component`
- 백엔드 : `NestJS`, `TypeORM`, `MySQL`, `Passport`, `Swagger`

# Trouble Shootings

## Frontend

### Issue #1

서버로부터 전달받은 데이터를 Redux store에 저장하여 상태값을 관리하였습니다. 그러던 중에 정보가 최신화되지 않는 이슈가 발생하였는데, 그 이유는 ~ 때문이었습니다.

> 왜 발생한 것인지?

따라서, 기존의 Redux store를 사용하지 않고, 특정 페이지에 접속할 때 해당 페이지에 필요한 데이터만 받아오도록 로직을 수정하여 해결하였습니다.

> 이렇게 해결한 구체적인 이유는?

### Issue #2

사용자 편의 측면에서 Object 형식의 데이터를 하나의 페이지에서 조회하고, 수정할 수 있도록 하나의 컴포넌트에서 렌더링하도록 구현하였습니다. 렌더링 과정에서 오류를 발생시키지 않도록 하기 위하여 상태값을 Object 형식으로 초기화하였는데, 서버로부터 전달받은 데이터로 업데이트되지 않는 이슈가 발생하였습니다.

이러한 이슈가 발생한 이유는 ~이었습니다.

> 왜 발생한 것인지?

따라서, Custom Hook을 사용하여 서버로부터 데이터를 받아오는 역할과 이 데이터를 렌더링하는 컴포넌트를 분리하였습니다. 이를 통해 각각 역할에 따라 서로 다른 파일에 코드가 존재하므로, Pull Request 시 충돌 발생이 줄어들었고, 코드의 가독성이 높아졌음을 알 수 있었습니다. 또한, 서버로 데이터를 받아오는 부분을 Custom Hook으로 분리하였기 때문에 다른 파일에서 동일한 기능을 사용해야 하는 경우 해당 Custom Hook만 import하면 되므로 코드의 재사용성이 증가하였음을 알 수 있었습니다.
