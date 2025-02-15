# Ethernaut - Foundry Template
**Ethernaut** 문제 틀잡기 귀찮은 자를 위한 **Foundry** 템플릿입니다.  
내부 블록체인을 구동하셨다면, 이 템플릿을 참고하여 문제 풀이를 진행해주세요. 
정상 동작 확인을 위해 contracts 폴더 안에서 `forge test`를 시도해 주세요.

---

## 폴더 위치

아래의 경로에 폴더를 넣어주세요
- **Exploit**: `contracts/src/
- **Script**: `contracts/scripts/

---

## 공격 스크립트 실행

```shell
forge script <TargetScript>:<ContractName> \
  --fork-url http://127.0.0.1:8545 \
  --broadcast \
  --contracts <TargetContractPath>
```

### 예시

```shell
forge script scripts/exploit/InstanceExploit.s.sol:InstanceExploit \
  --fork-url http://127.0.0.1:8545 \
  --broadcast \
  --contracts src/exploit/ExploitInstance/ExploitInstance.sol
```

---

## 키 설정
각 문제에 해당하는 PRIVATE_KEY와 INSTANCE_ADDRESS 정보를 넣어야 합니다.

`.env` 파일에 아래와 같이 키를 설정하세요.

```
PRIVATE_KEY=0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80
INSTANCE_ADDRESS=0xa8CB3Fa9110c3d9104DAC4B720928352F6a373dC
PLAYER_ADDRESS=0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
```

## 컨트랙트 인터페이스 사용
각 문제의 인터페이스를 사용할 수 있습니다.

``` solidity
// 컨트랙트 인터페이스 설정
Instance InstanceContract = Instance(payable(instance));


// 인터페이스에 정의된 인스턴스 함수 호출
InstanceContract.authenticate(InstanceContract.password());
// 인스턴스에 금액 전송
address(InstanceContract).call{value: 1 wei}("");
	
```