<img width="789" src ="https://user-images.githubusercontent.com/83544570/182020694-76570a8d-3341-4bc4-ba46-b2881df88e50.png"/>

### 🐥 프론트, 백엔드 깃허브

> [팀 프로젝트 프론트엔드 GitHub](https://github.com/wecode-bootcamp-korea/35-1st-9roomdroom9-frontend)<br/> [팀 프로젝트 백엔드 GitHub](https://github.com/wecode-bootcamp-korea/35-1st-9roomdroom9-backend)

### 🐥 앞뒤가 똑같은 구방문방구!

- 앞뒤가 똑같은 구방문방구를 팀명으로 팀원들의 물건을 재미있게 판매하는 서비스 홈페이지 구현했어요!
- 짧은 프로젝트 기간, 적은 인원으로 개발에 집중해야 하므로, 디자인/기획 부분만 모티브 삼아 진행했어요!
- 외부 라이브러리를 최대한 활용하지 않고 초기세팅부터 직접 구현했으며, 백엔드와 API까지하여 기능을 구현했어요!

#

### 🐥 하루같이 느껴 졌던 프로젝트 기간

2022.07.18(월) ~ 2022.07.29(금)

#

### 🐥 한분한분이 소중한 우리 팀 일원!

Front-End : 👑엄성훈님(PM), ❤️김광희님, 🐥정예빈님<br>
Back-end : ⚽️이정훈님, 🐱음정민님

#

### 🐥 Front-End 사용한 기술 스택!

<img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=HTML5&logoColor=white"/> <img src="https://img.shields.io/badge/CSS-1572B6?style=flat-square&logo=CSS3&logoColor=white"/>
<img src ="https://img.shields.io/badge/SASS-cc6699?style=flat-square&logo=Sass&logoColor=white"/>
<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=JavaScript&logoColor=white"/>
<img src="https://img.shields.io/badge/react-61DAFB?style=flat-square&logo=react&logoColor=black">

#

### 🐥 열심히 만들어본 페이지! 그래서 누가했는가!<br/>

#### [👑엄성훈님(PM)](https://velog.io/@fortheher/%EB%B0%B0%EB%AF%BC%EB%AC%B8%EB%B0%A9%EA%B5%AC-%ED%81%B4%EB%A1%A0-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-REACT), [❤️김광희님](https://tail-star.tistory.com/9), [🐥정예빈님](https://velog.io/@yebin214/1%EC%B0%A8-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%ED%9A%8C%EA%B3%A0)<br>

- (클릭 시 블로그로 이동!)
- Navigation Bar ❤️👑
- Footer ❤️
- **회원가입 페이지 👑**
- **로그인 페이지 👑**
- 메인 페이지 🐥
- **상품 리스트 페이지 👑**
- **상품 디테일 페이지 👑**
- 장바구니 페이지 ❤️

#

### 👑 저의 담당페이지 입니다!

#### 1. 카테고리 메뉴 페이지 이동 기능 구현

- categoryList 객체를 만들고 페이지 고유 ID를 부여하였고, text로 메뉴리스트를 구현하였습니다.
- categoryHandle()함수를 만들고 navigat()를 사용하여, 직접적으로 해당 ID 카테고리 페이지로 이동하도록 구현하였습니다.
- 예)엔드포인트 http://localhost:3000/products/<카테고리 id>

![카테고리페이지](https://user-images.githubusercontent.com/83544570/196182917-2dd98267-c439-428c-9c70-6d5ce8da381d.gif)

```jsx
const categoryList = [
  { id: 1000, text: '전체' },
  { id: 1, text: '문구' },
  { id: 2, text: '책/매거진F' },
  { id: 3, text: '구방그린' },
  { id: 4, text: '구방친구들' },
  { id: 5, text: '콜라보레이션' },
  { id: 6, text: '명예의 전당' },
];

const categoryHandle = (id) => {
  navigate(`/products/${id}`);
};

<nav className='category'>
  <ul className='nav-ul'>
    {categoryList.map((categoryList, i) => {
      return (
        <li
          onClick={() => {
            CategoryHandle(categoryList.id);
          }}
          key={categoryList.id}
        >
          {categoryList.text}
        </li>
      );
    })}
  </ul>
</nav>;
```

#### 2. 상품 리스트 정렬 기능 구현 / 상품 Badge (True or False)에 따른 적용 구현

- 백엔드에 fetch로 data를 요청, 응답 결과를 받아, useParams() 사용하여, id를 받아 Query String으로 onClick() Event로 적용하였습니다.
- 상품 밑에 표시되는 is_best(베스트 제품), is_green(친환경 제품) 불린값의 따라 화면에 나오도록, 삼항연산자를 적용하였습니다.

![정렬](https://user-images.githubusercontent.com/83544570/196174433-9bf42c69-d33c-41a0-9247-4c04c9aa38c3.gif)

```jsx
const sortLow = () => {
  fetch(`${BASE_URL}/products/${params.id}?sorting=LOW_PRICE`)
    .then(res => res.json())
    .then(data => {
      setList(data);
    });
};

 <button className="button-recommend"
   onClick={() => { sortLow(); }}>낮은 가격순
 </button>

 <div className="badge">
   {listData.is_best === true ? (<span className="badge-best">BEST&nbsp;</span>) : (<span className="badge-green" />)}
   {listData.is_green === true ? (<span className="badge-green">GREEN</span>) : (<span className="badge-best" />)}
 </div>
```

#### 3. 회원가입 유효성 검사 기능 구현

- 폼(Form) 핸들링

![회원가입](https://user-images.githubusercontent.com/83544570/196191488-bef40c3b-2dd8-4ed3-8ea8-736e6ca2ea58.gif)

- JOIN_INPUT_DATA 상수 타입을 지정하여, 각 input의 리스트요소를 만들었습니다.
- Input의 리스트들은 map()을 사용하여, 필요한 값들을 지정해 주었습니다.

```jsx
const JOIN_INPUT_DATA = [
{
  id: 1,
  name: 'userId',
  type: 'eamil',
  placeholder: '이메일',
  valid: '아이디로 사용 할 이메일을 입력해주세요',
  autoFocus: true,
},
{
  id: 2,
  name: 'userPw',
  type: 'password',
  placeholder: '비밀번호',
  valid: '새 비밀번호를 꼭 입력해주세요.',
  autoFocus: false,
},
....
];

{JOIN_INPUT_DATA.map(input => {
 return (
   <li key={input.id}>
     <div className="input-box-error">
      <input
       onChange={handleInput}
       name={input.name}
       type={input.type}
       placeholder={input.placeholder}
       autoFocus={input.autoFocus}
       autocomplete="off"
      >
      <p className="text-valid">{input.valid}</p>
     </div>
   </li>);})
}
```

#

- User의 입력값은 input 필드에 바인딩 하기위해 useState()로 초기값을 연결하였고, (ES6)구조분해할당으로 사용할 객체 값들을 분해하였습니다.
- Input의 필드가 변경되면 handleInput() 함수가 inputValue 갱신하도록 하였습니다.
- (ES6)계산된 속성명을 사용하여, 불변성을 유지 후, [name]:value의 name을 동적으로 사용하였습니다.

```jsx
const [inputValue, setInputValue] = useState({
  userId: '',
  userPw: '',
  pwCheck: '',
  userName: '',
  userPhoneNumber: '',
  userBirthday: null,
});

const { userId, userPw, pwCheck, userName, userPhoneNumber, userBirthday } =
  inputValue;

const handleInput = (e) => {
  const { name, value } = e.target;
  setInputValue({ ...inputValue, [name]: value });
};
```

#

- 동적으로 오류메시지를 띄우고 싶었으나, 실력이 부족하여 하지 못하였습니다.
- 구글링을 통해 정규식을 간단히 학습하였고, &&로 필드 값을 검사하도록 하였습니다.

```jsx
const REGEX_EMAIL = /^[a-zA-Z0-9+-_.]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+$/;
const REGEX_PASSWORD =
  /^(?=.*[A-Za-z])(?=.*\d)(?=.*[?!@#$%*&])[A-Za-z\d?!@#$%*&]{8,}$/;
const REGEX_NAME = /^[가-힣]{2,5}$/;
const REGEX_PHONE_NUMBER = /^01([0|1|6|7|8|9])-([0-9]{3,4})-([0-9]{4})$/;
const REGEX_BIRTHDAY =
  /^(19\d{2}|20\d{2})-(0[0-9]|1[0-2])-(0[1-9]|[1-2][0-9]|3[0-1])$/;

const isValid =
  REGEX_PASSWORD.test(userPw) &&
  pwCheck === userPw &&
  REGEX_NAME.test(userName) &&
  REGEX_EMAIL.test(userId) &&
  REGEX_PHONE_NUMBER.test(userPhoneNumber) &&
  (REGEX_BIRTHDAY.test(userBirthday) || userBirthday === null);
```

#

- form 최상위 요소에 onSubmit()으로 바인딩 된 Data를 백엔드에게 제출을 처리하였습니다.
- SyntheticEvent의 기본동작 새로고침을 막기위해, e.preventDefault() 적용하였습니다.
- 모든 필드값의 정규식을 통과하면, css 버튼 속성의 색상이 바뀌도록 button:disabled 활용하였습니다.
- 백엔드의 응답 결과에 따라 alert으로 user값이 있는지 없는지 구분처리 하였습니다.

```jsx
<form className='join-form' onSubmit={postUserData}>
  <button className='join-button-submit' disabled={!isValid}>
    회원가입
  </button>
</form>;

const postUserData = (e) => {
  e.preventDefault();
  fetch(`${BASE_URL}/users/signup`, {
    method: 'POST',
    body: JSON.stringify({
      name: userName,
      email: userId,
      mobile_number: userPhoneNumber,
      password: userPw,
      birthday: userBirthday,
    }),
  })
    .then((res) => res.json())
    .then((result) => {
      if (result.message === 'SUCCESS') {
        alert('회원 가입을 환영합니다!');
        navigate('/Login');
      } else if (result.message === 'KEY_ERROR') {
        alert('무슨 에러일까요? 테스트해봐요');
      } else if (result.message === 'EXIST_MOBILE_NUMBER') {
        alert('이미 존재하는 핸드폰 번호입니다.');
      } else if (result.message === 'EXIST_EMAIL') {
        alert('이미 존재하는 이메일 입니다.');
      } else if (result.message === 'INVALID_NAME') {
        alert('이름을 다시 확인해주세요.');
      }
    });
};
```

#### 4. 로그인시 Navbar 유저의 닉네임 상태 변화

- 로그인시 localStorage에 유저토큰을 저장하여, useEffect로 state값으로 할당 해주었습니다.
- user & 로그인 닉네임, 조건부 랜더링과 삼항연산자로 로그인 로그아웃을 구현하였습니다.

![로그인](https://user-images.githubusercontent.com/83544570/196624939-96b41251-1797-493e-81a7-5e5d088070f8.gif)

```jsx
fetch(`${BASE_URL}/users/login`, {
    method: 'POST',
    body: JSON.stringify({
      email: userId,
      password: userPw,
    }),
  })
    .then(res => res.json())
    .then(result => {
      if (result.access_token) {
        localStorage.setItem('token', result.access_token);
        localStorage.setItem('name', result.name);
        alert(`로그인을 환영합니다 ${userId}님`);
        navigate('/');

useEffect(() => {
  setToken(localStorage.getItem('token'));
  setUser(localStorage.getItem('name'));
}, []);

 <ul className="nav-icon">
   {user &&
     (<li className="nav-username">
       <span>{user}님</span></li>
    )}
 </ul>
```

#### 5. Path parameters를 이용한 제품 상세페이지와 탭 메뉴 구현

- 동적 라우팅을 위해 파라미터로 해당 번호의 :id를 연결해 주었습니다.
- 페이지에 필요한 데이터를 useEffect 에서 fetching하였고, state에 담아 컴포넌트 UI를 render 처리해 주었습니다.

![장바구니](https://user-images.githubusercontent.com/83544570/196631966-c560f988-f489-41bf-a852-a4902a775aa7.gif)

```jsx
<Route path='/Products/detail/:id' element={<ItemDetail />} />;

const params = useParams();

useEffect(() => {
  fetch(`${BASE_URL}/products/detail/${params.id}`)
    .then((res) => res.json())
    .then((data) => {
      setItemInfo(data.result);
    });
}, [params.id]);
```

#

- 탭 메뉴 구현을 위하여 상수데이터를 만들었고, 탭을 클릭했을때를 위해 state 초기값으로 1을 넣어주었습니다.
- onClick 이벤트로 onClick={() => clickHandler(idx + 1) setState 처리를 해주었습니다.

```jsx
const CATEGORY_ARR = [
 {
  id: 1,
  category: '상품정보',
  className: 'productInfo',
 },
 {
  id: 2,
  category: '기본정보',
  className: 'productInfoBasic',
  }, ...

const MAPPING_OBJ = {
  1: <First data={itemData} />,
  2: <Second />,
  3: <Third />,
};

const [currentId, setCurrentId] = useState(1);

const clickHandler = id => {
  setCurrentId(id);
};

<div className="item-detail-tabs">
  <ul>
   {CATEGORY_ARR.map((category, idx) => {
     return (
       <li
         key={category + idx}
         className={category.className}
         onClick={() => clickHandler(idx + 1)}
       >
       {category.category}
       </li>);
    })}
   </ul>
   {MAPPING_OBJ[currentId]}
</div>
```

#

### 🔥 <10월 ~ 추가내용> 리액트 기본기를 다시 공부했으며, 못했던 것들을 추가로 기록합니다.

### 회원가입 유효성 검사 동적 UI 오류메세지를 표현 못한 부분.

- 처음에는 공부량도 부족했고, 조건부 랜더링과 삼항연산자를 잘 활용하지 못하여, 동적으로 오류를 보여주는 컴포넌트를 만들지 못하였다.
- 정규식표현.test 메서드를 배열화 시켜주었고, map의 index를 이용해 REGEX_ARRAY[i]를 삼항연산자로 처리해 주었다.

![re로그인](https://user-images.githubusercontent.com/83544570/196650900-4d16463f-88f2-431b-8cb3-a3c0bf0af39e.gif)

```jsx
const REGEX_ARRAY = [
 REGEX_EMAIL.test(userId),
 REGEX_PASSWORD.test(userPw),
 pwCheck.length === 0 ? false : pwCheck === userPw,
 REGEX_NAME.test(userName),
 REGEX_PHONE_NUMBER.test(userPhoneNumber),
];

<ul className="join-form-list">
  {JOIN_INPUT_DATA.map((input, i) => {
    return (
     <li key={input.id}>
       <div className="input-box-error">
          <input
            onChange={handleInput}
            name={input.name}
            type={input.type}
            placeholder={input.placeholder}
            autoFocus={input.autoFocus}
            autocomplete="off"
           />
        </div>
         {REGEX_ARRAY[i] ? ('') : (
          <p className="text-valid">{input.valid}</p>)}
       </li>);
   })}
</ul

```

#

### 카테고리 메뉴에 동적인 UI를 CSS를 주지 못한 부분. +10.12

- 기존에 동적인 className을 이용하여 동적인 CSS 부분을 잘 다루지 못한것이 문제점임을 알게 되었다.
- state에 초기값을 전체로 주고, 클릭시 삼항연산자를 이용해 className에 active CSS를 주었다.

![동적UI메뉴](https://user-images.githubusercontent.com/83544570/196666943-c3949980-4a30-4fee-887f-af020da97cb6.gif)

```jsx
const categoryList = [
  { id: 1000, text: '전체' },
  { id: 1, text: '문구' },
  { id: 2, text: '책/매거진F' },
];

const [category, setCategory] = useState('전체');

const CategoryHandle = (id, category) => {
  navigate(`/products/${id}`);
  setCategory(category);
};

<ul className='nav-ul'>
  {categoryList.map((categoryList, i) => {
    return (
      <li
        className={category === categoryList.text ? 'active' : ''}
        onClick={() => {
          CategoryHandle(categoryList.id, categoryList.text);
        }}
        key={categoryList.id}
      >
        {categoryList.text}
      </li>
    );
  })}
</ul>;
```

#

### 서버에서 데이터 fetching 과정에서의 `!data <div>로딩중..<div> `으로만 표현한 부분. +10.19

- 비동기 API 요청 동안, 무엇을 나타내야하는지 잘 몰랐고, 어떻게 처리하면 좋은 방법들이 있는지 용어도 잘 몰랐다.
- `구글링을 잘 활용을 못한 것 같고, 공부후에는 Suspense, Spinners, Skeleton 등 여러표현이 있는걸 알게되었다.`
- 가장 자주 보이는 skeleton를 직접 만들기 위해 구글링 결과 keyframes과 gif 방식으로 넣는 것을 알 수 있었다.
- 라이브러리도 써봐야하지 않겠는가 싶어서 react-loading-skeleton 설치후 적용하였다.
- Array.from({ length: 10 }, v=> {e}) 간단히 유사배열을 만들고 갯수만큼 처리 하였다.

![스켈로톤UI](https://user-images.githubusercontent.com/83544570/196680766-9cac5b24-4376-4514-afbe-0c9de4a1333c.gif)

```jsx
import Skeleton from 'react-loading-skeleton';

!data === 0 || undefined (
  <div className="item-list-img-list">
    {Array.from({ length: 10 }, v => (
      <div className="item-list-img">
        <div className="links-wrap">
          <div className="links">
          <Skeleton width="282px" height="282px" />
        </div>
      </div>
    ))}
  </div> )
```

#

### 상품 리스트 정렬 기능과 상품 Badge(True or False)에 따른 적용 구현하는 부분 +10.21

- 기존은 템플릿 리터럴과 함수 인자 활용 그리고 조건부 랜더링을 미숙함을 보여주는 부분이였다.
- 인자에 sort('NEW'), sort('HIGH_PRICE')를 넣어서 해결하였고, 동시에 ?sorting=${sortPrice}로도 처리할 수 있었다.
- 기존 뱃지의 화면은 삼항연산자를 우겨넣어서, 어떤상황이든 무엇이든 badge-green과 badge-best의 빈값이 남아있었다.
- 그결과 CSS가 빈값에도 스타일값이 들어가고, 가운데 정렬이 안되는것이였다.
- 조건부랜더링으로 값이 있고 없고 할 때만 처리를 하여서 해결할 수 있었다.
- `공부하다 보이는 아쉬운 점들 비동기처리의 try..catch 예외처리와 버튼 같은것들은 하나의 컴포넌트로 props로 내려주는것에 따라 바뀌게 처리하면 더 좋은 코드가 될 수 있을 것 같다.`

```jsx
전
const sortLow = () => {
  fetch(`${BASE_URL}/products/${params.id}?sorting=LOW_PRICE`)
    .then(res => res.json())
    .then(data => {
      setList(data);
    });
};

 <button className="button-recommend"
   onClick={() => {sortLow()}}>낮은 가격순
 </button>

 <div className="badge">
   {listData.is_best === true ? (<span className="badge-best">BEST&nbsp;</span>) : (<span className="badge-green" />)}
   {listData.is_green === true ? (<span className="badge-green">GREEN</span>) : (<span className="badge-best" />)}
 </div>
```

```jsx
후
  const sort = sortPrice => {
    fetch(`${BASE_URL}/products/${params.id}?sorting=${sortPrice}`)
      .then(res => res.json())
      .then(data => {
        setList(data);
      });
  };

  <button className="button-least" onClick={() => {sort('NEW')}}>최신순</button>
  <button className="button-high" onClick={() => {sort('HIGH_PRICE')}}>높은 가격순</button>
  <button className="button-low" onClick={() => {sort('LOW_PRICE')}}>낮은 가격순</button>

  <div className="badge">
    {listData.is_best && <span className="badge-best">BEST</span>}
    {listData.is_green && (<span className="badge-green">GREEN</span>)}
  </div>
```

#

### 데이터 검색기능 +10.21

- 사용자가 입력하는 inputState 값과 비동기로 받아오는 SearchState로 관리를 하였다.
- setter변수에 받아오는 값들을 getter변수인 userSearch으로 넣어주었고, 그 값들을 filter함수와 retrun 값으로 includes 함수를 넣어주어 검색어가 입력되게 처리하였다.
- 상품의 값이 보이는 것은 input.length > 0 ? 길이와 삼항연산자로 처리하였다.
- `검색을 테스트 하다보니 잘 작동되지 않았던 것은 빠르게 검색을하면 값을 불러오지 못했다. 아직 해결하지 못한 부분.`
- `공부를 하다보니 검색은 실시간으로 요청을 하기 때문에, 성능을 향상 시키려면 Debounce처리릃 하면 성능을 향상시킬 수 있다고 한다. 공부해두자.`

![search](https://user-images.githubusercontent.com/83544570/202481384-0d617940-30d9-4b3c-92a4-ae3b6875cf07.gif)


```jsx
const [userInput, setUserInput] = useState('');
const [userSearch, setUserSearch] = useState([]);

useEffect(() => {
  fetch(`${BASE_URL}/products/1000?search=${userInput}`)
    .then((response) => response.json())
    .then((result) => {
      setUserSearch(result.products_data);
    });
}, [userInput]);

const handleChange = (e) => {
  setUserInput(e.target.value);
};

const filterInputValue = userSearch.filter((search) => {
  return search.name.includes(userInput);
});

<div className='searchResultContainer'>
  {userInput.length > 0 ? (
    filterInputValue.map((list) => {
      return (
        <SearchItems
          key={list.id}
          list={list}
          handleSearchBarOn={handleSearchBarOn}
        />
      );
    })
  ) : (
    <div className='searchBarRecentContainer'>
      <section className='searchBarRecentItems'>
        <h3>검색어를 입력해주세요</h3>
      </section>
    </div>
  )}
</div>;
```

#

### Netlify로 배포하며 겪은 Mixed content ? +10.22

- 해당 문제는 mixed content는 암호화된 HTTPS 기반의 사이트에서 암호화되지 않은 HTTP 사이트에 요청을 보내서 Mixed content 에러가 발생한 것이라고 한다.
- 엔드포인트의 경우 http였고, Netlify의 요청은 https를 요청하고 있었다.
- 이 오류도 CORS 처럼 백엔드에서의 처리방법과 프론트서버에서의 처리 방법이 있었다.
- netlify에서 지원하는 proxy를 설정하여 우회처리 할 수 있었다.
- root에 netlify.toml 파일을 생성후 redirect 처리.

![error](https://user-images.githubusercontent.com/83544570/202397419-3f8bda64-242c-46ec-a758-5fda6e693b4e.png)

```jsx
[[redirects]];
from = '/proxy/*';
to = 'http://0.000.000.00:8000/:splat';
status = 200;
force = true;

const PROXY = window.location.hostname === 'localhost' ? '' : '/proxy';

useEffect(() => {
  fetch(`${PROXY}/products/1000?search=${userInput}`)
    .then((response) => response.json())
    .then((result) => {
      setUserSearch(result.products_data);
    });
}, [PROXY, userInput]);
```

### 🐥 재밌게 만들었어요!

> [유튜브 영상 링크](https://www.youtube.com/watch?v=MYvWzDs-gTM)(처음 만든 버전입니다.)

<table>
  <thead>
    <tr>
      <th>
        메인상단
      </th>
      <th>
        메인하단
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">
        <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182020741-6f4576ee-148d-4fdb-b730-887ce6b865d7.png">
      </td>
      <td align="center">
          <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182020750-e4aa16af-2898-4fdd-b180-0273db42c56c.png">
      </td>
    </tr>
  </tbody>
</table>
<table>
  <thead>
    <tr>
      <th>
        회원가입
      </th>
      <th>
        로그인
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">
        <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182020941-d1b3dbc5-de36-41b1-819b-f6967cc620d3.png">
      </td>
      <td align="center">
          <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182020960-0ef6a9f6-bb8b-4ca9-8da6-e3a042c1e93e.png">
      </td>
    </tr>
  </tbody>
</table>
<table>
  <thead>
    <tr>
      <th>
        상세페이지
      </th>
      <th>
        상세페이지 별 탭
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">
        <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182020992-ea26c2a4-c458-4ad0-ad25-95b97ff085e6.png">
      </td>
      <td align="center">
          <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182020994-cdfc557d-b91e-478e-9c3c-1cb550f55480.png">
      </td>
    </tr>
  </tbody>
</table>
<table>
  <thead>
    <tr>
      <th>
        장바구니 페이지
      </th>
      <th>
        장바구니 텅
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
     <td align="center">
        <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182021059-191b8339-4381-4a0a-af04-d7ecc5aa42fd.png">
      </td>
      <td align="center">
        <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182021057-89a57cac-9878-4e01-b570-55aad72efbee.jpg">
      </td>
    </tr>
  </tbody>
</table>

#

### 🐥 우리 어떻게 일 한 한거야?

- GitHub : 각 페이지마다 branch를 생성하여 관리했어요!

- Slack : 슬랙과 깃허브를 연동하여 상시 상황을 공유하도록 했어요!

- Trello : 각자 맡은 구현부분을 티켓으로 만들어 진행 상황을 공유했어요!

- Notion : 매일 아침 30분정도 갖는 회의에 원활한 소통을 위해 하루계획, 현재진행상황, 팀원칭찬 등 여러부분을 작성했어요!

<table>
  <thead>
    <tr>
      <th>
        트렐로
      </th>
      <th>
        노션
      </th>
    </tr>
       <tr>
      <th>
        깃허브
      </th>
      <th>
        슬랙
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center">
        <img width="789" alt="image" src="https://user-images.githubusercontent.com/105622173/182006289-fd28d445-bdd3-42bf-9e85-a49fcfe6db61.png">      
        </td>
      <td align="center">
        <img width="789" alt=image" src="https://user-images.githubusercontent.com/105622173/182006668-76b57624-26d5-46ec-b91d-a2545d22c5d3.png">      
        </td>
    </tr>
      <tr>
      <td align="center">
        <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182021461-f653661b-b65f-439d-8487-18b8b3ed476d.jpg">      
        </td>
      <td align="center">
        <img width="789" alt="image" src="https://user-images.githubusercontent.com/83544570/182021475-8a2a1f6f-7187-4189-a171-e62426a6ff47.png">      
        </td>
    </tr>
  </tbody>
</table>

#

### 🐥 Reference

- 이 프로젝트는 배민 문방구 사이트를 참조하여 학습목적으로 만들었습니다.
- 학습용으로 만들었기 때문에 이 코드를 활용하여 이득을 취하거나 무단 배포할 경우 법적으로 문제될 수 있습니다.
- 이 프로젝트에서 사용하고 있는 사진 대부분은 위코드에서 구매한 것이므로 해당 프로젝트 외부인이 사용할 수 없습니다.
