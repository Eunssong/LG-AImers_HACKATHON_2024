# 데이터 살펴보기

- Data Sample : 59,299개
- features : 29개

# 데이터 문제 및 해결전략

## 데이터 불균형 해결하기
![image](https://github.com/Eunssong/LG-AImers_HACKATHON_2024/assets/134351442/fc1e2f9d-547e-40e2-9708-9b1b3964c8db)
- 타겟 변수의 데이터 불균형이 심하다. 
- 불균형을 맞춰주는 전략이 필요하다. -> undersampling으로 하기엔, 버려지는 데이터가 너무 많은데, 이를 살릴 방법을 고려해보자. 


## 데이터 결측치 
![image](https://github.com/Eunssong/LG-AImers_HACKATHON_2024/assets/134351442/ce8dd691-52c1-471f-96f7-7d68c333d09d)    

P: 데이터를 살펴보니 결측치가 상당히 높음을 확인 할 수 있음.
  
S:
- id_strategic_ver(ID), it_strategic_ver(IT)은 Business Unit 보고 채울 수 있을 것 같음 -> idit_strategic_ver은 둘 중에 하나라도 1이면 1값을 가짐.
- 위의 변수의 결측치를 채우고 idit_strategic_ver 하나의 변수로 대체하는 접근 방법 고려해보기
- 이후에, ver_win_ration_per_bu 변수 결측치 채우는데 사용가능한지 확인해보기. -> nan 값 확인하기

P: custom_country와 custom_country.1(대륙)은 확인해보니 동일한 데이터 값을 가짐.  

![image](https://github.com/Eunssong/LG-AImers_HACKATHON_2024/assets/134351442/db6f441f-c4fd-45e7-a514-5d43236a8eb7)
![image](https://github.com/Eunssong/LG-AImers_HACKATHON_2024/assets/134351442/dcadda20-82ac-47e1-b8fe-e806d5379b02)   

- 두 변수 모두 결측치에 대해 동일한 index값을 가지는 것 또한 확인할 수 있음.
     
S: 
- 두개의 변수 중에 하나만 사용 할 수 있음.
- 데이터 값의 도시명은 날리고, 나라명만 살려도 될 것 같다.
- 결측치에 대해서는 response_corporation하고 비교하여 채울 수 있을 것 같다. -> 아니면 두 변수 날리고 response_corporation만 사용해도 될 것 같다.

![image](https://github.com/Eunssong/LG-AImers_HACKATHON_2024/assets/134351442/fe2cfe66-0e81-44e0-ad9f-dc26dcfe966e)


## 데이터 전처리
- customer_type에 End customer과 End-customer값이 있는데 값 통일하기 -> 다른 변수들도 값 확인 필요하다.
- column drop할지 고민해보기
  - ver_cus와 customer_type 관계 고려
  - ver_pro와 product_categroy 관계 고려


# 가설 세우기
- 베이스라인 모델이 decision_tree로 주시긴 했지만, 적절할까?
- bant_submit이 0 인 값과 is_converted 와 관계는? -> 상관관계는 매우 0에 가까운 값을 가진다. 선형관계성이 보이지는 않는다.
- 지난 거래 기록과 is_converted와 관계가 있지 않을까?
- 타겟 변수와 연관된 주요 변수는 뭘까? 
