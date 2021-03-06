cmake_minimum_required(VERSION 3.0)
project(BrainShockSTL)


set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -pthread")

option(BUILD_TEST "Build the unit tests" ON)

add_executable(Chapter7_Section01 section01_set.cpp)
add_executable(Chapter7_Section02 section02_multiset.cpp)
add_executable(Chapter7_Section03 section03_map.cpp)
add_executable(Chapter7_Section04 section04_multimap.cpp)

enable_testing()

add_test(Chapter7_Section01 Chapter7_Section01 -o "result1.xml" -r "xml")
add_test(Chapter7_Section02 Chapter7_Section02 -o "result2.xml" -r "xml")
add_test(Chapter7_Section03 Chapter7_Section03 -o "result3.xml" -r "junit")
add_test(Chapter7_Section04 Chapter7_Section04 -o "result4.xml" -r "junit")

# arg 값이 잘못되어 no test run (catch에서)상태가 되어도 ctest 는 passed로 처리한다.
## 잘못 입력된 값이지만 성공한 예
### add_test(CatchTutorial_02 Test_CatchTutorial_02 "[vectoc][resize]")  # 원래 결과는  no test run 이어야 함.
### add_test(CatchTutorial_02 Test_CatchTutorial_02 "[vectoc]")          # 원래 결과는  no test run 이어야 함.
## 실패 결과가 제대로 나오는 예
### add_test(CatchTutorial_02 Test_CatchTutorial_02 "[vector]")  # 원래 결과는  no test run 이어야 함.

# console로 output 을 받는 테스트는 argument 를 입력해도 정보를 볼 수 없다

# 하지만 결과리포트를 파일로 받을 수 있다
## -o "${outputfile}" -r "${report way}" 를 주면 결과를 파일로 받을 수 있다 [console(default) | junit | xml | compact ]
## 대신 add_test 하나당 다른 파일 이름으로 받도록 해야한다. (뒤에걸로 덮어 쓴다)
