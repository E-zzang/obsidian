```java
Scanner scanner = new Scanner(System.in);
String input = scanner.nextLine();

try {
	BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
	StringTokenizer st =new StringTokenizer(br.readLine());
	int N = Integer.parseInt(st.nextToken());
	int L = Integer.parseInt(st.nextToken());
	int[][] map = new int[N][N];
	int[][] map2 = new int[N][N];
	//맵 생성
	for(int i=0;i<N;i++) {
		StringTokenizer st1 =new StringTokenizer(br.readLine());
		for(int j=0;j<N;j++) {
			map[i][j] = Integer.parseInt(st1.nextToken());
			map2[j][i] = map[i][j];
		}
	}
} catch (IOException e) { // 예외처리 필수
  e.printStackTrace();
  System.out.println(e.getMessage());
}

```
