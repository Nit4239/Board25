# 발견 문제점
## 1. Run ass Spring app 시 unsatisfieddependencyexception 발생

> **원인** : WriteDAO.xml 파일의 view.do resultType 오기



//수정
...ResultType="com.lec.spring.writeDTO">
->...resultType="com.lec.spring.domain.WriteDTO">


## 2. update 수정 성공 후 status 400 오류 발생

> **원인** : updateOK.jsp파일의 수정 성공 후 href경로 오류

//수정
view.do?uid=${uid} -> view.do?uid=${param.uid}

## 3. 글작성 시 작성자 란 미기입 해도 글작성이 성공하는 상황

> **원인** : write.jsp파일의 if절 return 미입력

//수정
if(name =="") {
    alert("작성자 란은 반드시 입력해야 합니다");
    frm['name'].focus();
}
->
if(name =="") {
    alert("작성자 란은 반드시 입력해야 합니다");
    frm['name'].focus();
    return false;
}

## 4. 글삭제 시 status 500 에러

> **원인** : WriteDAO.xml의 deletbyuid의 sql문 오타

//수정
DELETE FROM test_write WHERE uid={uid}
->
DELETE FROM test_write WHERE wr_uid={uid}