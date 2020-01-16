## 관계형 데이터 모델링

#### MODEL = 어떠한 목적을 가지고 진짜를 모방 한것

#### Modeling = 표에 데이터를 담는것

1. Data Modeling 
				
> 문제를 현실로부터 뜯어내서 고도의 추상화 과정을 거쳐서 그것을 컴퓨터라는<br>
새로운 현실로 옮겨담는 작업 현실과 컴퓨터는 서로 다르기 때문에,<br>
처음에 해결하려고 했던 문제가 데이터 베이스 표에 잘담겨 있는지를 확인하는 작업을 끊임없이 하여야 한다.		

#### 업무파악 
				
> 개념적 데이터 모델링 -> 논리적 데이터 모델링 -> 물리적 데이터 모델링

### 1. 개념적 데이터 모델링
						
> 하고자 하는 일에 어떠한 개념들이 있고, 각각의 개념들이 서로 어떻게 상호 작용하고 있는지<br>
심사 숙고 해보는시간 ER Diagram 이라는 초석을 만들어 내는것
						 
### 2. 논리적 데이터 모델링
						
> 관계형 데이터 베이스 패러다임에 맞는 표로써 우리가 생각했던 개념을 표로써<br>
전환하는 작업을 논리적 데이터 모델링 이라고 한다.
						
### 3. 물리적 데이터 모델링
							
> 1.  어떠한 데이터베이스 제품을 사용할 것인지 선택하고,<br>
그 데이터베이스 제품에 최적화된 코드를 사용하여 실제 표를 만드는것
							
> 2.  산출물을 위한 표를 생성할수 있는 SQL의 코드를 갖게되는 것이 물리적 데이터 모델링의 최종적인 목적이다.
							
### 개념적 모델링 
				
- ERD : Entity Relationship Diagram (독립체들의 관계를 도표로 나타낸것)
							
### 기능
>1. 매우 쉽게 표로 전환할 수있도록 도와준다.
								
>2. ERD 수 세월 동안 다듬어진 정교한 규칙들이 적립되어 있어 ERD를 만든다면 표로 만드는것은 어렵지 않다.
								
#### 1. 정보 
										
> 정보를 발견하고 그것을 다른 사람들에게 표현 할수 있도록 도와준다.
#### 2. 그룹
										
> 서로 연관된 정보를 그룹핑 하여 인식하고 이것을 다른사람에게 표현할수 있도록 도와준다.
									
#### 3. 관례
										
> 정보 그룹 사이의 관계를 인식하고 그것을 다른 사람에게 표현할수 있도록 도와준다.
| 드라마 제목 | 주연 배우 | 방영일 |
|:----------:|:----------:|:----------:|						  

### 표현
| ERD | -> | SQL |
|:----------:|:----------:|:----------:|
|Entity|->|Table|									 
|Attribute|->|Column|									
|Relation|->|PK, FK|									 
|Tuple|->|Row|
														
					
### Identifier : Primary Key [식별자]
							
### 1. 인조키(대리키)[시퀀스] 

> 행이 추가될 때마다 자동으로 1씩 증가 시켜서 중복되지 않는 값을 부여하는 것을 통해서 식별자를 제공할수 있다. 
								
### 2. 후보키(Candidate Key) : 	
| - | - | - |
|:----------:|:----------:|:----------:|
| email    | national_id |  일때   user_id, email, national_id 는 후보키(Candidate Key)|
|a@mail.c | 100001|user_id 는 기본키(Primary Key) |								
|b@mail.c | 100002|email, national_id 는 대체키(Alternate Key)|
								
3. 중복키(Composite Key)
한가지 키 만으로 식별이 불가할때 중복되는 것을 합쳐서 식별할수 있는데 이것을 중복키라고 한다. 
							
Cardinality(기수) : 하나의 Entity가 참여할 수 있는 관계의 수 - 1:1 1:다 다:다
							
Optionality(선택성) : 있을수도, 없을수도 있다.
							
저자		댓글	- 이- ER다이어그램에서 
								
예시)	Kim			댓글1		Optional : 예시에서 저자는 댓글이 있을수도, 없을수도 있다 	 	O로 표현
Lee			댓글2										
Park		댓글3		Mandatory : 예시에서 댓글은 바드시 저자가 있다.				|로 표현
				
### 3. 논리적 데이터 모델링

### 1. Mapping Rule
				
표현 	 

>Entity      -> 	Table
									 
>Attribute   ->	Column  
									
>Relation    -> 	PK, FK
									 
>Tuple       -> 	Row
											
						
1. 1:1 관계의 처리
							
- 저자, 휴먼저자
							
저자와 휴먼저자가 있다고 가정 할때 저자는 휴먼저자가 있을수도 없을수도 있지만(Optional)
							  
휴먼저자는 저자가 반드시 있어야 한다.(Mandatory)
						
### 2. 1:N 관계의 처리
						
- 저자, 글, 댓글
							
저자와 글 그리고 댓글이 있다고 가정 할때 
							  
저자는 댓글이 있을수도 있고 없을수도 있다.(Optional)
							  
그리고, 글 또한 댓글이 댓글이 있을수도 있고, 없을수도 있다.(Optional)
							  
그러나, 댓글은 글, 저자가 반드시 있어야만 한다.(Mandatory)
					
### 3. N:M 관계의 처리
							
- 저자, 책, (쓰기)
							
1. N:M 관계에서는 애매한 상황이 발생하는데 이러한 상황에서 Mapping Table 생성하여 해결해 준다.
							
서로 공통된 컬럼을 생성하여 테이블에 입력한다. Mapping Table(Write Table)을 작성하게 되면 
								
이 두개의 Table이 결합되었을때 의미가 있는정보 예로 각각의 저자가 그 글을 언제 수정하기 시작하였는가
								
와 같은 정보를 추가 하여 줄수있다.
								
2. 저자와 책 그리고 추가된 Mapping Table(작성 기능)가 있다고 가정 할때
							 
저자는 작성을 할수도 있고, 안할수도 있다.(Optional)
								
책은 작성을 할수도 있고, 안할수도 있다.(Optional)
								
작성 기능 저자가 있어야만하고, 책이 있어야만 한다.(Mandatory)

							
### 4. 물리적 데이터 모델링
				
>1. 정규화
					
- UNF -> 1NF -> 2NF -> 3NF -> 4NF -> 5NF -> 6NF 순차적으로 정규화 한다.
					
1. UNF (Un Normalize Form)
						
- 정규화가 적용되어 있지 않은 형태의 표를 의미한다.						   
						 
2. 1NF (1st Normalize Form) 
						
- Atomic Columsn 를 만족한다면 제1 정규형에 속한다.
						   
						 
3. 2NF (2nd Normalize Form) 
						 
- 1NF를 만족시키고, NoPartial Dependencies 를 만족한다면 제2 정규형에 속한다.
						
4. 3NF (3rd Normalize Form)  

- 2NF를 만족시키고, No Transitive Dependencies 를 만족한다면 제3 정규형에 속한다.
						 
5. 4NF (4th Normalize Form) 
						
- 3NF를 만족시키고, Every non-trivial,multi-value dependency has a superkey 를 만족한다면 제4 정규형에 속한다.
						
6. 5NF (5th Normalize Form) 
						
- 4NF를 만족시키고, Every non-trivial join dependency is implied by a candidate key를 만족한다면 제5 저규형에 속한다.
						
7. 6NF (6th Normalize Form) 
						
- 5NF를 만족시키고, Ecry join dependency is trivial을 만족한다면 제 6 정규형에 속한다.
