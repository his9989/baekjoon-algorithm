## 백준 알고리즘 1978번. 1로 만들기

* 문제: 주어진 수 N개 중에서 소수가 몇 개 인지 찾아서 출력하는 프로그램을 작성하시오

* 입력: N은 100이하, 주어지는 수는 1000이하의 자연수이다.

* 출력: 주어진 수 중 소수의 개수를 출력한다.


<code>

	#include<iostream>
	using namespace std;

	int main() {

		int num = 0, i, j;								// num: 몇 개의 값을 입력할지 지정하는 수. 
		int check = 1;									// 소수 여부를 파악하는 논리변수 역할
		int count = 0;									// 소수의 개수를 저장하는 변수
		cin >> num;									// 몇 개의 값에 대해 소수 여부를 파악할지 결정하는 범위 변수

		int * arr = NULL;								// 동적 배열
		arr = new int[num];

		for (i = 0; i < num; i++) {							// 동적 배열에 소수 여부 파악할 수를 num개 입력
			cin >> arr[i];
		}

		for (i = 0; i < num; i++) {							// 주어진 num개의 수에 대해 prime number 여부를 파악하는 알고리즘
			if (arr[i] == 1) count += 0;						// 1인 경우, 소수가 아니다.
			else if (arr[i] == 2) count += 1;					// 2인 경우, 소수다.
			else {									// 3이상의 경우
				check = 1;							// 일단은 모든 경우가 소수라고 가정.
				for (j = 2; j < arr[i]; j++) {					// 2부터 "주어진수-1"에 대해, "주어진 수"로 나누어 떨어지는지 여부를 파악.
					if (arr[i] % j == 0) { check = 0; break;}		// 나누어 떨어지는 경우, 소수가 아님을 알았으며, arr[i]에 대한 소수 여부 파악 알고리즘을 끝낸다.
					else check = 1;						// 나누어 떨어지지 않으면, 소수라고 가정한다.
				}
				if (check == 1) count += 1;					// 결과가 소수로 나오면, 소수 개수를 하나 추가한다.
			}
		}

		cout << count << endl;								// 소수 개수 출력.

		return 0;
	}

</code>
