참고 링크 :
- https://ulfrid.github.io/python/python-sqlalchemy/
- https://velog.io/@baeyuna97/SQLAlchemy-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0

SQLAlchemy
---
SQLAlchemy는 파이썬에서 사용되는 오픈 소스 SQL 툴킷 및 Object-Relational Mapping(ORM) 라이브러리이다.

### 장점
1. 객체지향적인 코드로 비즈니스 로직에 집중 가능
2. 재사용 및 유지보수 편리성이 증가
3. DBMS에 대한 종속성이 줄어듦
4. 코드 가독성 상승

### 단점
1. ORM만으로 서비스를 구현하기 어려움
2. 프로시저가 많은 시스템에서는 장점을 가져가기 어려움
3. 호출 방식에 따라 성능이 크게 차이가 있음

#### Install
```
pip install sqlalchemy
```

#### 예시 코드
```
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.orm import sessionmaker
from sqlalchemy.ext.declarative import declarative_base

# 데이터베이스 연결 설정
DATABASE_URL = "sqlite:///example.db"
engine = create_engine(DATABASE_URL)
Session = sessionmaker(bind=engine)

# 데이터베이스 모델 정의
Base = declarative_base()

class User(Base):
    __tablename__ = 'users'

    id = Column(Integer, primary_key=True)
    username = Column(String)
    email = Column(String)

# 데이터베이스 테이블 생성
Base.metadata.create_all(engine)

if __name__ == "__main__":
    # 데이터베이스 세션 생성
    session = Session()

    # 사용자 추가
    new_user = User(username="john_doe", email="john@example.com")
    session.add(new_user)
    session.commit()

    # 사용자 조회
    users = session.query(User).all()
    for user in users:
        print(f"User ID: {user.id}, Username: {user.username}, Email: {user.email}")

    # 세션 닫기
    session.close()
```

`SQLAlchemy`는 범용적인 ORM 및 SQL 툴킷으로 다양한 SQL 데이터베이스 시스템과 작업할 수 있도록 설계된 반면 `Django ORM`은 Django 웹 프레임워크 개발 시 사용된다.
