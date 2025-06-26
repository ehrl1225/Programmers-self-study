Postman을 둘러보다가 발견한 방법인데

TDD방식으로 테스트가 가능하다.

Request에서 Scripts로 들어가

Post-response 탭으로 들어가면 스크립트를 짤 수 있는데

```javascript
pm.test("Response has required fields", function () {

    const responseData = pm.response.json();

    pm.expect(responseData).to.be.an('object').that.includes.all.keys('id', 'createDate', 'modifyDate', 'content');

});
```
이 방식으로 작성하면 테스트가 가능하다.
