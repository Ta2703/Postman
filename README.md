# Postman
HW_1

Создать запросы в Postman.

Protocol: http
IP: 162.55.220.72
Port: 5005

EP_1
Method: GET
EndPoint: /get_method
request url params: 
 name: str
 age: int

response: 
[
    “Str”,
    “Str”
]

==================

EP_2
Method: POST
EndPoint: /user_info_3
request form data: 
 name: str
 age: int
 salary: int

response: 
{'name': name,
          'age': age,
          'salary': salary,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'u_salary_1_5_year': salary * 4}}


==================

EP_3
Method: GET
EndPoint: /object_info_1
request url params: 
 name: str
 age: int
 weight: int

response: 
{'name': name,
          'age': age,
          'daily_food': weight * 0.012,
          'daily_sleep': weight * 2.5}


==================

EP_4
Method: GET
EndPoint: /object_info_2
request url params: 
 name: str
 age: int
 salary: int

response: 
{'start_qa_salary': salary,
          'qa_salary_after_6_months': salary * 2,
          'qa_salary_after_12_months': salary * 2.7,
          'qa_salary_after_1.5_year': salary * 3.3,
          'qa_salary_after_3.5_years': salary * 3.8,
          'person': {'u_name': [user_name, salary, age],
                     'u_age': age,
                     'u_salary_5_years': salary * 4.2}
          }


==================

EP_5
Method: GET
EndPoint: /object_info_3
request url params: 
 name: str
 age: int
 salary: int

response: 
{'name': name,
          'age': age,
          'salary': salary,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'pets': {'cat':{'name':'Sunny',
                                     'age': 3},
                              'dog':{'name':'Luky',
                                     'age': 4}},
                     'u_salary_1_5_year': salary * 4}
          }


==================

EP_6
Method: GET
EndPoint: /object_info_4
request url params: 
 name: str
 age: int
 salary: int

response: 
{'name': name,
          'age': int(age),
          'salary': [salary, str(salary * 2), str(salary * 3)]}


==================

EP_7
Method: POST
EndPoint: /user_info_2
request form data: 
 name: str
 age: int
 salary: int

response: 
{'start_qa_salary': salary,
          'qa_salary_after_6_months': salary * 2,
          'qa_salary_after_12_months': salary * 2.7,
          'qa_salary_after_1.5_year': salary * 3.3,
          'qa_salary_after_3.5_years': salary * 3.8,
          'person': {'u_name': [user_name, salary, age],
                     'u_age': age,
                     'u_salary_5_years': salary * 4.2}
          }

# HW_2Postman

<http://162.55.220.72:5005/first>

1. Отправить запрос.
2. Статус код 200
3. Проверить, что в body приходит правильный string.

<http://162.55.220.72:5005/user_info_3>

1. Отправить запрос.
2. Статус код 200.

в сниппетах(Snippets) выбрать Status code: Code is 200

```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

3. Спарсить response body в json.
```
var responseData = pm.response.json();
console.log(responseData);
```

4. Проверить, что name в ответе равно name s request (name вбить руками.)
В сниппетах выбрать Response body: JSON value check
```
pm.test("name s request", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.name).to.eql("Tamara");
});
```
5. Проверить, что age в ответе равно age s request (age вбить руками.)
В сниппетах выбрать Response body: JSON value check
```
pm.test("age s request", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.age).to.eql('28');
});
```
6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
Response body: JSON value check
```
pm.test("salary s request", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.salary).to.eql(1000);
});
```
7. Спарсить request.
```
var requestData = request.data;
console.log(requestData);
```
8. Проверить, что name в ответе равно name s request (name забрать из request.)
Response body: JSON value check
```
pm.test("name request", function () {
     var jsonData = pm.response.json();
    pm.expect(jsonData.name).to.eql(requestData.name);
});
```
9. Проверить, что age в ответе равно age s request (age забрать из request.)
Response body: JSON value check
```
pm.test("age s request", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.age).to.eql(requestData.age);
});
```
10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
Response body: JSON value check
```
pm.test("salary s request", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.salary).to.eql(Number(requestData.salary));
});
```
11. Вывести в консоль параметр family из response.
```
console.log(responseData.family);
```
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```
pm.test("u_salary_1_5_yea is salary*4", function () {
    pm.expect(responseData.salary*4).to.eql(Number(responseData.family.u_salary_1_5_year));
});
```
<http://162.55.220.72:5005/object_info_3>

1. Отправить запрос.
2. Статус код 200

```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
var responseData = pm.response.json();
console.log(responseData);
```
4. Спарсить request.
```
var requestData = pm.request.url.query.toObject();
console.log(requestData);
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)
Response body: JSON value check
```
pm.test("name s request", function () {
    pm.expect(responseData.name).to.eql(requestData.name);
});
```
6. Проверить, что age в ответе равно age s request (age забрать из request.)
```
pm.test("age s request", function () {
    pm.expect(responseData.age).to.eql(requestData.age);
});
```
7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
pm.test("salary s request", function () {
    pm.expect(responseData.salary ).to.eql(Number(requestData.salary ));
});
```
8. Вывести в консоль параметр family из response.
```
console.log(responseData.family);
```
9. Проверить, что у параметра dog есть параметры name.
```
pm.test("Dog has name", function () {
    pm.expect(responseData.family.pets.dog).to.haveOwnProperty('name');
});  
```
10. Проверить, что у параметра dog есть параметры age.
```
pm.test("Dog has age", function () {
    pm.expect(responseData.family.pets.dog).to.haveOwnProperty('age');
});  
```
11. Проверить, что параметр name имеет значение Luky.

```
pm.test("Your test name", function () {
    pm.expect(responseData.family.pets.dog.name).to.eql('Luky');
});
```
12. Проверить, что параметр age имеет значение 4.
```
pm.test("Age is 4", function () {
    pm.expect(responseData.family.pets.dog.age).to.eql(Number(4));
});
```
<http://162.55.220.72:5005/object_info_4>

1. Отправить запрос.
2. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

3. Спарсить response body в json.
```
var responseData = pm.response.json();
console.log(responseData);
```

4. Спарсить request.
```
var requestData = pm.request.url.query.toObject();
console.log(requestData);
```

5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("Name", function () {
    pm.expect(responseData.name).to.eql(requestData.name);
});
```

6. Проверить, что age в ответе равно age из request (age забрать из request.)
```
pm.test("Age", function () {
    pm.expect(responseData.age).to.eql(Number(requestData.age));
});
```

7. Вывести в консоль параметр salary из request.
```
console.log(requestData.salary);
```

8. Вывести в консоль параметр salary из response.
```
console.log(responseData.salary);
```

9. Вывести в консоль 0-й элемент параметра salary из response.
```
console.log(responseData.salary[0]);
```

10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```
console.log(responseData.salary[1]);
```

11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```
console.log(responseData.salary[2]);
```

12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
```
pm.test("Salary is correct", function () {
    pm.expect(responseData.salary[0]).to.eql(Number(requestData.salary));
});
```

13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
```
pm.test("Salary*2 is correct", function () {
    pm.expect(+responseData.salary[1]).to.eql(requestData.salary*2);
});
```

14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
```
pm.test("Salary*3 is correct", function () {
    pm.expect(+responseData.salary[2]).to.eql(requestData.salary*3);
});
```

15. Создать в окружении переменную name
```
На панели нажать Environment, Create new environment, присвоить окружению имя(New for HW_2)
В атрибут Variable внести строку name
```
16. Создать в окружении переменную age
```
В атрибут Variable внести строку age
```
17. Создать в окружении переменную salary
```
В атрибут Variable внести строку salary
```

18. Передать в окружение переменную name
```
pm.environment.set("name", responseData.name);
```
19. Передать в окружение переменную age
```
pm.environment.set("age", responseData.age);
```

20. Передать в окружение переменную salary
```
pm.environment.set("salary", responseData.salary[0]);
```

21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
```
for (let i of responseData.salary) {
    console.log('salary', i)
}
```

<http://162.55.220.72:5005/user_info_2>

1. Вставить параметр salary из окружения в request

```
Добавить новый запрос(Add request) Req_5
Выбрать метод Post, открыть вкладку Body, form-data
salary{{salary}}
```

2. Вставить параметр age из окружения в age
```
age{{age}}
```

3. Вставить параметр name из окружения в name
```
name {{name}}
```

4. Отправить запрос.
5. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```

6. Спарсить response body в json.
```
var responseData = pm.response.json();
console.log(responseData);
```
7. Спарсить request.
```
let requestData = request.data;
console.log(requestData);
```

8. Проверить, что json response имеет параметр start_qa_salary
```
pm.test("start_qa_salary", function () {
    pm.expect(responseData).to.haveOwnProperty('start_qa_salary');
});
```

9. Проверить, что json response имеет параметр qa_salary_after_6_months
```
pm.test("qa_salary_after_6_months", function () {
    pm.expect(responseData).to.haveOwnProperty('qa_salary_after_6_months');
});
```

10. Проверить, что json response имеет параметр qa_salary_after_12_months
```
pm.test('qa_salary_after_12_months', function() {
    pm.expect(responseData).to.haveOwnProperty('qa_salary_after_12_months')
});
```

11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
```
pm.test('qa_salary_after_1.5_year', function(){
    pm.expect(responseData).to.haveOwnProperty('qa_salary_after_1.5_year')
});
```

12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
```
pm.test('qa_salary_after_3.5_years', function(){
    pm.expect(responseData).to.haveOwnProperty('qa_salary_after_3.5_years')
});
```

13. Проверить, что json response имеет параметр person
```
pm.test('person', function(){
    pm.expect(responseData).to.haveOwnProperty('person');
})
```

14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
```
pm.test("start_qa_salary is correct", function () {
    pm.expect(responseData.start_qa_salary).to.eql(Number(requestData.salary));
});  
```

15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
```
pm.test("qa_salary_after_6_months", function () {
    pm.expect(responseData.qa_salary_after_6_months).to.eql(requestData.salary*2);
});
```

16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
```
pm.test("qa_salary_after_12_months", function () {
    pm.expect(responseData.qa_salary_after_12_months).to.eql(requestData.salary*2.7);
});
```

17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
```
pm.test("qa_salary_after_1.5_year", function () {
    pm.expect(responseData['qa_salary_after_1.5_year']).to.eql(requestData.salary*3.3);
});
```

18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
```
pm.test("qa_salary_after_3.5_years", function () {
    pm.expect(responseData['qa_salary_after_3.5_years']).to.eql(requestData.salary*3.8);
});
```

19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
```
pm.test("person 1 u_name", function () {
    pm.expect(responseData.person.u_name[1]).to.eql(Number(requestData.salary));
});
```

20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
```
pm.test("u_age", function () {
    pm.expect(responseData.person.u_age).to.eql(Number(requestData.age));
});
```

21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
```
pm.test("u_salary_5_years ", function () {
    pm.expect(responseData.person.u_salary_5_years).to.eql(requestData.salary*4.2);
});
```

22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
```
for (let i in responseData.person) {
    console.log('person', i);
}
```
