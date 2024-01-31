# <div align="center">**SSANDE NFT Repository**</div>

# 로컬 백엔드 url용 .env 생성

front 폴더안에 .env 만들어주세요

```
REACT_APP_BACK_URL='http://localhost:4000'
```

# 배포서버 url용 .env.production 생성

fromt 폴더안에 .env.production 만들어주세요

```
REACT_APP_BACK_URL='배포서버 주소'
```


# 폴더구조

![화면 캡처 2023-02-15 094419](https://user-images.githubusercontent.com/97073355/218896004-245a8d5f-f04f-4b0c-8afc-c94ee07c49d2.png)







back 폴더
```
NFT 민팅해줄 이미지가 들어있습니다
```

blockchain 폴더
```
remix-ethereum IDE 에서 sol파일을 만들고 검증해서 
blockchain 폴더에 담아줬습니다
```

front 폴더
```
컴포넌트와 페이지
back 과 blockchain을 이어주는 프론트 기능들이 들어있습니다
```

server 폴더
```
AWS에 등록할 build 폴더가 들어있습니다
```

# Ssande - NFT Minting, Trade, Auction Project

## 🖥️ Project Page

<li><a href = "https://ssande-d5c60.web.app/">http://15.164.231.206</a></li>
<br><br>

## 📒 Documents

 <li><a href = "https://www.notion.so/SSANDE-NFT-1-a9586595f1d64cdea197634ee21f8d06">📖Project Info</a></li>
 <br><br>

## 🧾 Project Description

3인으로 구성된 팀으로 일주일간 진행한 프로젝트.<br>
ERC721 Token(NFT)민팅 구현 및

<br><br>

## 🏗️ Project Structure

![image](https://user-images.githubusercontent.com/107898015/218940897-f58aa2bb-ecc2-4065-a0c4-49ee75d37e8e.png)
<br><br>

## 🛠 Tech Stack

<img src="https://img.shields.io/badge/Solidity-purple?style=flat-square&logo=Solidity&logoColor=white"> <img src="https://img.shields.io/badge/OpenZeppelin-purple?style=flat-square&logo=OpenZeppelin&logoColor=white"> <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=React&logoColor=white"/> <img src="https://img.shields.io/badge/React Router-61DAFB?style=flat-square&logo=ReactRouter&logoColor=white"/> <img src="https://img.shields.io/badge/React Router-61DAFB?style=flat-square&logo=ReactContext&logoColor=white"/> <img src="https://img.shields.io/badge/Axios-61DAFB?style=flat-square&logo=Axios&logoColor=white"/> <img src="https://img.shields.io/badge/Node.js-yellow?style=flat-square&logo=Node.js&logoColor=white"/> <img src="https://img.shields.io/badge/.env-yellow?style=flat-square&logo=.env&logoColor=white"/>
<br><br>

## 🎨 Preview

![ezgif com-video-to-gif (1)](https://user-images.githubusercontent.com/97073355/218945995-c08d52a2-614b-49f0-b482-b3d367ec2921.gif)
<img width="1499" alt="image" src="https://user-images.githubusercontent.com/107898015/218937998-7a3f64c9-da9c-4300-a330-8a5b08425cc8.png">
<img width="1481" alt="image" src="https://user-images.githubusercontent.com/107898015/218936915-973fa1d4-e5a6-428a-b466-d0321ee572e6.png">
<br><br>

## 목차

1. [3D Slide](#3D-Slide)

2. [Connect Wallet](#Connect-Wallet)

3. [Modal && Minting](#Modal-&&-Minting)

---

### 3D Slide

<!-- <br><br><br><br><br><br><br><br><br><br><br><br> -->
```JS

유명한 NFT사진들로  3D 느낌이 나게 구현해봤습니다

.moveImg {
	width: 100%;
	position: absolute;
	float: right;
	animation: rotar 15s infinite linear;
	transform-style: preserve-3d;
    
}

각각 이미지에 nth-child로 지정해준다음 위치를 정해놓고
사진들을 오른쪽으로 돌게하는 animation 효과와 preserve-3d
마지막으로 @keyframes 으로 rotateY 값을 넣어주면 멋진 3d-slide를 만들수 있습니다
```

### Connect Wallet
<br>

![asdasd](https://user-images.githubusercontent.com/97073355/218951174-69cf3424-08f9-4479-be10-170e9a5c84c0.png)


```JS
메타마스크에 연결할 수 있는 버튼입니다


  const onConnect = async () => {
    try {
      const currentProvider = detectCurrentProvider();
      if (currentProvider) {
        if (currentProvider !== window.ethereum) {
        }
        await currentProvider.request({ method: 'eth_requestAccounts' });
        const web3 = new Web3(currentProvider);
        const userAccount = await web3.eth.getAccounts();
        const chainId = await web3.eth.getChainId();
        const account = userAccount[0];
        let ethBalance = await web3.eth.getBalance(account);
        ethBalance = web3.utils.fromWei(ethBalance, 'ether');
        saveUserInfo(ethBalance, account, chainId);
        if (userAccount.length === 0) {
        }
      }
    } catch (err) {}
  };

  const onDisconnect = () => {
    window.localStorage.removeItem('userAccount');
    setUserInfo({});
    setIsConnected(false);
  };

지갑에 연동하게해주는 onConnenct 함수와 
지갑이랑 연동시  "지갑연동" 글자가 -> "해제하기"로 바뀌게 되면서
지갑을 연동을 해제 할 수 있는 onDisconnect함수를 만들었습니다

```
![ezgif com-video-to-gif](https://user-images.githubusercontent.com/97073355/218985250-592e8d44-4008-41b1-b0bf-47ec54a6a88d.gif)


지갑연결을 하면 보유한 이더와 계정주소를 확인할 수 있습니다.

<br>

### Modal && Minting

<br>

![ezgif com-video-to-gif (1)](https://user-images.githubusercontent.com/97073355/220283276-ff88f8ed-3b9b-4f94-a0ce-3418a026f5ef.gif)

<br>
민팅 버튼을 누르면 모달창이 나오고 민팅할 NFT 갯수를 정할 수 있습니다

민팅 갯수에 따라 설정한 Goerli이 빠져나갑니다.



<br>

### NFT Card

<br>

<img width="1499" alt="image" src="https://user-images.githubusercontent.com/107898015/218937998-7a3f64c9-da9c-4300-a330-8a5b08425cc8.png">

```JS

 { 
  saleTokenURIs &&
            Object.keys(saleTokenURIs).map(tokenId => (

              <Col key={tokenId} lg="3" md="4" sm="6" 

              className="mb-4">
                <ShopNftCard key={tokenId} tokenId={tokenId} tokenURI={saleTokenURIs[tokenId]} />
              </Col>
            ))}
```
<br>
 saleTokenURIs 객체의 모든 항목에 대해 ShopNftCard 컴포넌트를 렌더링하여 NFT 토큰을 표시합니다.

<br>

 NFT 사진은 배경화면, 몸 , 눈 , 입모양으로 나뉘어서 직접 만들었고 Hashlips 에서 만든 코드를 이용해서 수백가지의 이미지를 추출했습니다


## Contract

컨트렉트 구조

![image](https://user-images.githubusercontent.com/107898015/221673138-e0304bf8-b2db-44b2-8f0a-951496e029e9.png)

![image](https://user-images.githubusercontent.com/107898015/221672828-9bdf2129-0807-43b2-9849-985c9dfd9cdc.png)

<br>

### Token Contract

<br>
Batch 민팅시 발생하는 가스비를 획기적으로 줄인 ERC721A-Standard를 활용하였다.

![image](https://user-images.githubusercontent.com/107898015/221669596-6418031d-f4a2-4cd7-9fdc-d8b0a163dbca.png)
![image](https://user-images.githubusercontent.com/107898015/221669714-f196894f-0e62-4cca-866b-ee7be1b63b63.png)

위 그림과 같이 ERC721Enumerable은 민팅갯수에 따라 가스비가 비례적으로 증가하지만 ERC721A는 동시에 몇개를 민팅하던간에 가스비가 비슷하게 소모된다는 것을 알 수 있다.

이렇게 가스비를 획기적으로 줄일수 있는 이유는

1. 2개이상의 토큰(NFT)을 한번에 민팅할때 owner(address)의 balance(소유한 토큰의 갯수)값을 한번만 업데이트 한다.

2. 2개이상의 토큰(NFT)을 한번에 민팅할때 토큰(tokenId)의 owner(address)값을 한번만 업데이트한다.<br>
   예를들어 아래그림처럼 100번토큰부터 3개를 한번엔 뽑아도 100번토큰의 owner만 storage에 기록해놓는다.
   ![image](https://user-images.githubusercontent.com/107898015/221672267-19c00539-221d-4fbb-88c2-6c3aa0e3315c.png)

<br>
<br>

### Trade Contract(일반거래)

<br>

일반판매를 위한 storage 변수값은 딱 매핑 하나만 사용하였다. (가스비 최적화를 위하여)

```js
mapping(uint => uint) private _tokensOnSale;
```

판매중인 토큰의 아이디값들을 담아놓는 배열을 따로 만들지 않았기때문에

현재 발행된 모든토큰들을 순회하며 발행된 토큰들만 걸러주는 함수를 따로 만들었다.

이렇게 함수로써 대체할수 있던 이유는 ERC721A규격으로 생성된 토큰ID값은 순차적으로 배정된다는 특징 때문.

```js
function onSaleList() external view returns(uint256[] memory){
        uint256[] memory tokensOnSale = new uint256[](_countOnSale()); // 배열크기 미리배정
        uint256 index = 0;

        for(uint tokenId = 1; tokenId <= Token.totalSupply(); tokenId++) {
            if(isOnSale(tokenId)) {
                tokensOnSale[index] = tokenId;
                index ++;
            }
        }

        return tokensOnSale;
    }
```

일반 거래의 기능은 딱 구매, 판매 ,판매취소 세가지이고, 판매자는 수수료를 제외한 금액을 정산받게 설정하였다.

```js
uint256 incomeAfterFee = afterFee(price);
(bool success, ) = tokenOwner.call{value: incomeAfterFee}("");
require(success, "payment failed");
```

<br>
<br>

### Trade Contract(경매거래)

<br>

#### <경매 로직>

- 경매에 등록을 원하는 사람은 최소금액과 경매시간 두가지를 정해서 경매에 등록한
  이때 토큰의 소유는 그대로 본인에게 있고, 토큰전송에대한 권한을 컨트렉트에 넘김.

- 입찰을 원하는 사람은 최소금액 이상의 가격으로만 입찰할수있고,
  입찰시 입찰액은 자신의 지갑에서 빠져나가며,
  자신의 입찰가보다 높은 입찰가가 들어오면 본인의 입찰액은 자동으로 환불됨.

- 경매에 등록한 사람이 정한 경매시간이 지나고나면,
  경매는 마감되고 입찰자가 아무도 없는 경매는 그대로 유찰됨.

- 입찰자가 있을경우에는 해당 경매는 정산되지않은 경매로 분류되게되고,
  입찰자나 판매자 둘중에 아무나 한명이정산버튼을 누르게되면,
  입찰자에게는 토큰이 판매자에게는 수수료가 제외된 판매금이 전송됨.
  <br>
  <br>

