다. 최적회귀방정식의 선택, 설명변수의 선택

* 설명변수는 x1, x2, x3...
* 반응변수는 y

1. 선택방법
   1. 모든 가능한 조합의 회귀분석 (All possible regression)
2. 단계적 변수선택 (Stepwise Variable Selection)
   1. 전진선택법, 하나씩 추가
   2. 후진제거법, 하나씩 제거
   3. 단계적별방법, 단계별로 추가 제거
3. 방법
   1. 회귀식 만들기 `lm(종속변수~ 설명변수1+설명변수2, data=데이터세트)`
   2. 만든회귀식 `c <- lm(y ~ x1+x2, data=df)`
   3. `step(lm(종속변수~ 설명변수1+설명변수2, data=데이터세트), scope = list(lower=~1, upper=~설명변수1+설명변수2), direction="변수선택방법")`
   4. 위에꺼 말고 아래껄로
   5. `step(lm(종속변수 ~1, 데이터세트명), scope = list(lower=~1, upper=~설명변수1+설명변수2), direction="변수선택방법")`
   6. 변수선택방법
      1. forward
      2. both
      3. backward

```r
step(lm(y ~1, df), scope=list(lower=~1, upper=~x1+x2+x3+x4), direction="forward")
```

```r
step(lm(time ~1, hills), scope=list(lower=~1,upper=~dist+climb),direction="forward")
```

```r
step(lm(pemax ~나이+키+체중+BMP+RV+FRC+TLC, data = Bio), direction="backward")
```

```r
step(lm(pemax ~1, data = Bio), scope=list(lower=~1,upper=~나이+키+체중+BMP+RV+FRC+TLC) direction="both")
```


기출 출처
* 1과목
  * https://gaiag.tistory.com/43?category=293781
* 2과목
* 3과목
* http://blog.naver.com/PostView.nhn?blogId=tjsqjavmfh&logNo=220871647633&parentCategoryNo=&categoryNo=65&viewDate=&isShowPopularPosts=true&from=search