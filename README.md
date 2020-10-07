# Граф - матрица смежности

## Алгоритм:

- Выбор между графом ориентированным и неориентированным
- Задание двумерного массива размера N x N
- Присваивание вершинам графа названий
- Задание связей между вершинами
- Проверка на связность
- Вывод матрицы смежности
- Задание графа геометрическим способом через GraphViz

## Визуализация:
``` C
// запись на языке DOT

	char* arr = (char*) calloc(500, sizeof(char));

	if(bg == 1){
		strcat(arr, "digraph G {");
		for (int i = 0; i < n; i++){
		for (int j = 0; j < n; j++){
			if (mtx[i][j] > 0){
				for (int a = 0; a < mtx[i][j]; a++){
					strcat(arr, names[i]);
					strcat(arr, "->");
					strcat(arr, names[j]);
					strcat(arr, ";");
				}
			}
		}
	}
	}
	else {
		strcat(arr, "graph G {");
		for (int i = 0; i < n; i++){
			strcat(arr, names[i]);
			strcat(arr, ";");
		}
		for (int i = 0; i < n; i++){
			for (int j = i; j < n; j++){
				if (mtx[i][j] > 0){
					for (int a = 0; a < mtx[i][j]; a++){
						strcat(arr, names[i]);
						strcat(arr, "--");
						strcat(arr, names[j]);
						strcat(arr, ";");
					}
				}
			}
		}
		}

	strcat(arr, "}");

	FILE* f = fopen("graph.dot", "w");
	fprintf(f, "%s\n", arr);
	fclose(f);

	char* term = (char*) calloc(500, sizeof(char));

	strcat(term, "echo \"");
	strcat(term, arr);

	strcat(term, "\" | dot -Tpng >./graph_pikcha.png");
	system(term);
	free(term);
	free(arr);

```