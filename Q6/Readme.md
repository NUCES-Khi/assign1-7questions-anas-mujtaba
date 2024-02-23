# Assignment 1 : Question 6
|Std ID|Name|
|------|-|
|K22-8709|Mujtaba Junaid|
|K22-4049|Anas Soharwardy|

import heapq
#comments have been made to make code undertstandable
romania_map = {
    'Zerind': {'Arad': 75, 'Oradea': 71},
    'Arad' : {'Zerind': 75, 'Timisoara': 118, 'Sibiu': 140},
    'Oradea': {'Zerind': 71, 'Sibiu': 151},
    'Sibiu': {'Arad': 140, 'Oradea': 151, 'Fagaras': 99, 'Rimnicu Vilcea': 80},
    'Timisoara': {'Arad': 118, 'Lugoj': 111},
    'Lugoj': {'Timisoara': 111, 'Mehadia': 70},
    'Mehadia': {'Lugoj': 70, 'Drobeta': 75},
    'Drobeta': {'Mehadia': 75, 'Craiova': 120},
    'Craiova': {'Drobeta': 120, 'Rimnicu Vilcea': 146, 'Pitesti': 138},
    'Rimnicu Vilcea': {'Sibiu': 80, 'Craiova': 146, 'Pitesti': 97},
    'Fagaras': {'Sibiu': 99, 'Bucharest': 211},
    'Pitesti': {'Rimnicu Vilcea': 97, 'Craiova': 138, 'Bucharest': 101},
    'Bucharest': {'Fagaras': 211, 'Pitesti': 101, 'Giurgiu': 90, 'Urziceni': 85},
    'Giurgiu': {'Bucharest': 90},
    'Urziceni': {'Bucharest': 85, 'Vaslui': 142, 'Hirsova': 98},
    'Hirsova': {'Urziceni': 98, 'Eforie': 86},
    'Eforie': {'Hirsova': 86},
    'Vaslui': {'Urziceni': 142, 'Iasi': 92},
    'Iasi': {'Vaslui': 92, 'Neamt': 87},
    'Neamt': {'Iasi': 87}
} 



heuristics = {
    'Arad': 366,
    'Zerind': 374,
    'Oradea': 380,
    'Sibiu': 253,
    'Timisoara': 329,
    'Lugoj': 244,
    'Mehadia': 241,
    'Drobeta': 242,
    'Craiova': 160,
    'Rimnicu Vilcea': 193,
    'Fagaras': 176,
    'Pitesti': 100,
    'Bucharest': 0,
    'Giurgiu': 77,
    'Urziceni': 80,
    'Hirsova': 151,
    'Eforie': 161,
    'Vaslui': 199,
    'Iasi': 226,
    'Neamt': 234
}

def bfs(graph, start, goal): #breadth first search
    queue = [(start, [start])] #start points
    path_cost = 0

    while queue:
        current, path = queue.pop(0)
        path_cost += romania_map[current][path[-2]] if len(path) > 1 else 0  # take sum of path and check for inavlaid distances

        if current == goal: #if found then return
            return path, path_cost

        for neighbor in graph[current]:
            if neighbor not in path: #if not found then append for further evaluation
                queue.append((neighbor, path + [neighbor]))

    return None, None
def dfs(graph, start, goal):  # Depth-First Search
    stack = [(start, [start])]  # start points
    path_cost = 0

    while stack:
        current, path = stack.pop()
        path_cost += romania_map[current][path[-2]] if len(path) > 1 else 0  # take sum of path and check for invalid distances

        if current == goal:  # if found then return
            return path, path_cost

        for neighbor in graph[current]:
            if neighbor not in path:  # if not found then append for further evaluation
                stack.append((neighbor, path + [neighbor]))

    return None, None
def ucs(graph, start, goal):#uniform cost search
    priority_queue = [(0, start, [start])] #intialize start points 
    path_cost = 0

    while priority_queue:# work until evry co-ordinate is not visited
        cost, current, path = heapq.heappop(priority_queue)
        path_cost += cost  #sum if total cost as ucs keeps getting sum and looking for shortegt path amongst those.

        if current == goal: # if found then return 
            return path, path_cost

        for neighbor, edge_cost in graph[current].items():
            if neighbor not in path: # if not found then push for evaluation
                heapq.heappush(priority_queue, (cost + edge_cost, neighbor, path + [neighbor]))

    return None, None

def gbfs(graph, start, goal, heuristics): #greedy best first search
    priority_queue = [(heuristics[start], start, [start])] # priority based pn heuristics
    path_cost = 0

    while priority_queue:
        _, current, path = heapq.heappop(priority_queue)
        path_cost += romania_map[current][path[-2]] if len(path) > 1 else 0

        if current == goal: # if goal found, base case
            return path, path_cost

        for neighbor in graph[current]:
            if neighbor not in path: # if not visited and not the goal then push the distance for further evaluation
                heapq.heappush(priority_queue, (heuristics[neighbor], neighbor, path + [neighbor]))

    return None, None

def iddfs(graph, start, goal, max_depth):  # Iterative Deepening Depth-First Search
    for depth in range(max_depth + 1):
        path, path_cost = dfs(graph, start, goal)  # Using DFS asa helper function
        if path:
            return path, path_cost

    return None, None


def calculate_path_cost(graph, path):
    path_cost = 0
    for i in range(len(path) - 1):
        #cumulative sum of all co-ordinates of a path, basically a helper function of iterative depth first search
        path_cost += graph[path[i]][path[i + 1]]
    return path_cost



#As source and destination not given in qn , I have randomly assumed them
source = 'Arad' 
destination = 'Bucharest'

bfs_path, bfs_path_cost = bfs(romania_map, source, destination)
ucs_path, ucs_path_cost = ucs(romania_map, source, destination)
gbfs_path, gbfs_path_cost = gbfs(romania_map, source, destination, heuristics)
iddfs_path, iddfs_path_cost = iddfs(romania_map, source, destination, max_depth=10)

print("BFS Path:", bfs_path)
print("BFS Path Cost:", bfs_path_cost)
print()
print("UCS Path:", ucs_path)
print("UCS Path Cost:", ucs_path_cost)
print()
print("GBFS Path:", gbfs_path)
print("GBFS Path Cost:", gbfs_path_cost)
print()
print("IDDFS Path:", iddfs_path)
print("IDDFS Path Cost:", iddfs_path_cost)
#dictionary to find the ascending order of the paths of different algos.
results = [
    ("BFS",  bfs_path_cost),
    ("UCS", ucs_path_cost),
    ("GBFS", gbfs_path_cost),
    ("IDDFS", iddfs_path_cost)
]

sorted_results = sorted(results, key=lambda x: x[1])

print("The ascending order of the path of the algorithms are ", sorted_results)

Output:

![image](https://github.com/NUCES-Khi/assign1-7questions-anas-mujtaba/assets/160864816/15de1b0a-25d4-4e13-9d48-6df5e9f2f269)
 

