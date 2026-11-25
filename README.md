
#include <iostream>
#include <queue>
using namespace std;

int graph[5][5] = {
    {0, 1, 1, 0, 0},
    {1, 0, 0, 1, 1},
    {1, 0, 0, 0, 1},
    {0, 1, 0, 0, 0},
    {0, 1, 1, 0, 0}
};

int visited[5];

// DFS Function
void DFS(int vertex)
{
    cout << vertex << " ";
    visited[vertex] = 1;

    for (int i = 0; i < 5; i++)
    {
        if (graph[vertex][i] == 1 &&
            visited[i] == 0)
        {
            DFS(i);
        }
    }
}

// BFS Function
void BFS(int start)
{
    queue<int> q;

    for (int i = 0; i < 5; i++)
        visited[i] = 0;

    visited[start] = 1;
    q.push(start);

    while (!q.empty())
    {
        int vertex = q.front();
        q.pop();

        cout << vertex << " ";

        for (int i = 0; i < 5; i++)
        {
            if (graph[vertex][i] == 1 &&
                visited[i] == 0)
            {
                visited[i] = 1;
                q.push(i);
            }
        }
    }
}

int main()
{
    // DFS Traversal
    for (int i = 0; i < 5; i++)
        visited[i] = 0;

    cout << "DFS Traversal: ";
    DFS(0);

    // BFS Traversal
    cout << "\nBFS Traversal: ";
    BFS(0);

    return 0;
}
