# Evalstock
## <주식 종목 가치평가 프로그램>
<img src="https://user-images.githubusercontent.com/56333934/118797411-85f77a80-b8d7-11eb-8ed1-b93c22195316.png" width="300" height="300">

> 이 도서에서는 모멘텀 투자보다는 가치투자의 관점에서 투자의 방향을 이야기한다. 이론으로 정리된 가치 평가 방식을 파이썬을 활용하여 직접 개발해보았다.

**모멘텀 투자** 란 시장 분위기와 뉴스, 테마, 종목 정보, 투자 심리, 수급, 기술적 분석 등의 요소를 기반으로 하여서 투자자의 직관이나 영감을 합하여 자산 가격을 전망하고 이에 따라 투자하는 방법이다.

**가치 투자자** 는 자산 가격을 전망하지 않는 대신 자산의 가치를 분석하고 전망한다. 자산 가치 대비 현재 시장 가격이 충분히 낮을 경우 매수하고 가치 대비 가격이 높다고 판단될 경우 매도하는 방식입니다. 가치투자의 대표자로는 워런버핏과 피터 린치 등이 있다.

## Table of Methods
- [Methods](#methods)
  - [get_html](#get_html)
  - [get_excel_high_dividend](#get_excel_high_dividend)
  - [get_excel_siga_top](#get_excel_siga_top)
  - [df_extension](#df_extension)
  - [report](#report)
 
 
### get_html
- 사용자가 입력한 종목코드를 파라미터로 받아 comp.fnguide.com 에서 재무제표를 크롤링 한다.
![image](https://user-images.githubusercontent.com/56333934/118799121-56497200-b8d9-11eb-9dba-e692f763244d.png)

### get_excel_high_dividend
- 고배당주 리스트가 저장되어있는 엑셀을 로드 후 종목코드 리스트를 반환한다.

### get_excel_siga_top
- 시가총액 순위대로 저장되어있는 엑셀을 로드 후 종목코드 리스트를 반환한다.

### df_extension
- get_html에서 반환된 재무제표를 바탕으로 미래 재무제표를 예측하여 DataFrame을 2025년까지 연장한다.
- 전년도 BPS에 (평균 ROE)/100 를 곱해 새로운 EPS를 만들고, 전년도 BPS에 새로운 EPS를 더해 새로운 BPS를 만든다. 
![image](https://user-images.githubusercontent.com/56333934/118799881-3b2b3200-b8da-11eb-9d93-d8d2ffabfd7b.png)

### report
- 연장된 재무제표에서 마지막 년도 BPS에 원하는 수익률(여기선 15%)에 (연장된 기간)만큼 제곱한 값을 나누어 현재의 기업가치를 구한다.
- 현재의 기업가치가 현재 주가의 1.5배보다 크면 적합, 아니면 부적합을 Return한다.
 ![image](https://user-images.githubusercontent.com/56333934/118800631-18e5e400-b8db-11eb-8f4c-e2c1ffd6819d.png)
  
