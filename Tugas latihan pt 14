import networkx as nx
import matplotlib.pyplot as plt

# LATIHAN 1 - FRAUD ANALYSIS

print("=" * 50)
print("ANALISIS FRAUD - LATIHAN 1")
print("=" * 50)

# Buat graph
graph1 = nx.Graph()

# Tambahkan node dengan label 'F' (Fraud) atau 'NF' (Non-Fraud)
node_labels_1 = {
    1: 'F', 2: 'NF', 3: 'NF', 4: 'F', 5: 'F',
    6: 'NF', 7: 'F', 8: 'NF', 9: 'NF', 10: 'F'
}

for node, label in node_labels_1.items():
    graph1.add_node(node, status=label)

# Tambahkan edge sesuai diagram
edges_1 = [
    (1, 7), (1, 2), (2, 3), (2, 6), (3, 4), (3, 6),
    (6, 5), (7, 6), (7, 8), (7, 10), (8, 9)
]
graph1.add_edges_from(edges_1)

# Statistik dasar
total_nodes = graph1.number_of_nodes()
total_edges = graph1.number_of_edges()
fraud_count = sum(1 for n in graph1.nodes if graph1.nodes[n]['status'] == 'F')
nonfraud_count = total_nodes - fraud_count

print("\nStatistik Graph:")
print(f"Jumlah Node: {total_nodes}")
print(f"Jumlah Edge: {total_edges}")
print(f"Node Fraud: {fraud_count}")
print(f"Node Non-Fraud: {nonfraud_count}")
print(f"Rasio Fraud: {fraud_count/total_nodes:.2%}")

# Centrality analysis
deg_centrality = nx.degree_centrality(graph1)
bet_centrality = nx.betweenness_centrality(graph1)
clo_centrality = nx.closeness_centrality(graph1)

print("\n--- Top 3 Node berdasarkan Degree Centrality ---")
for node, cent in sorted(deg_centrality.items(), key=lambda x: x[1], reverse=True)[:3]:
    print(f"Node {node} ({node_labels_1[node]}): {cent:.3f}")

print("\n--- Top 3 Node berdasarkan Betweenness Centrality ---")
for node, cent in sorted(bet_centrality.items(), key=lambda x: x[1], reverse=True)[:3]:
    print(f"Node {node} ({node_labels_1[node]}): {cent:.3f}")

# Analisis koneksi Fraud-NonFraud
fraud_to_fraud = 0
fraud_to_nonfraud = 0
nonfraud_to_nonfraud = 0

for n1, n2 in graph1.edges():
    status1 = graph1.nodes[n1]['status']
    status2 = graph1.nodes[n2]['status']
    if status1 == 'F' and status2 == 'F':
        fraud_to_fraud += 1
    elif status1 == 'NF' and status2 == 'NF':
        nonfraud_to_nonfraud += 1
    else:
        fraud_to_nonfraud += 1

print("\n--- Analisis Koneksi ---")
print(f"Fraud-Fraud: {fraud_to_fraud}")
print(f"Fraud-NonFraud: {fraud_to_nonfraud}")
print(f"NonFraud-NonFraud: {nonfraud_to_nonfraud}")


# LATIHAN 2 - FRAUD ANALYSIS

print("\n" + "=" * 50)
print("ANALISIS FRAUD - LATIHAN 2")
print("=" * 50)

graph2 = nx.Graph()

node_labels_2 = {
    1: 'F', 2: 'F', 3: 'F', 4: 'NF', 5: 'NF',
    6: 'NF', 7: 'NF', 8: 'NF', 9: 'NF', 10: 'F',
    11: 'F', 12: 'F', 13: 'NF'
}

for node, label in node_labels_2.items():
    graph2.add_node(node, status=label)

edges_2 = [
    (1, 2), (1, 3), (2, 3), (2, 12), (3, 4), (3, 10),
    (3, 11), (4, 5), (4, 6), (4, 7), (5, 6), (5, 7),
    (5, 8), (6, 9), (7, 8), (7, 9), (8, 9), (10, 11),
    (12, 13)
]
graph2.add_edges_from(edges_2)

# Statistik dasar
total_nodes2 = graph2.number_of_nodes()
total_edges2 = graph2.number_of_edges()
fraud_count2 = sum(1 for n in graph2.nodes if graph2.nodes[n]['status'] == 'F')
nonfraud_count2 = total_nodes2 - fraud_count2

print("\nStatistik Graph:")
print(f"Jumlah Node: {total_nodes2}")
print(f"Jumlah Edge: {total_edges2}")
print(f"Node Fraud: {fraud_count2}")
print(f"Node Non-Fraud: {nonfraud_count2}")
print(f"Rasio Fraud: {fraud_count2/total_nodes2:.2%}")

# Centrality analysis
deg_centrality2 = nx.degree_centrality(graph2)
bet_centrality2 = nx.betweenness_centrality(graph2)

print("\n--- Top 3 Node berdasarkan Degree Centrality ---")
for node, cent in sorted(deg_centrality2.items(), key=lambda x: x[1], reverse=True)[:3]:
    print(f"Node {node} ({node_labels_2[node]}): {cent:.3f}")

print("\n--- Top 3 Node berdasarkan Betweenness Centrality ---")
for node, cent in sorted(bet_centrality2.items(), key=lambda x: x[1], reverse=True)[:3]:
    print(f"Node {node} ({node_labels_2[node]}): {cent:.3f}")

# Analisis koneksi Fraud-NonFraud
fraud_to_fraud2 = 0
fraud_to_nonfraud2 = 0
nonfraud_to_nonfraud2 = 0

for n1, n2 in graph2.edges():
    status1 = graph2.nodes[n1]['status']
    status2 = graph2.nodes[n2]['status']
    if status1 == 'F' and status2 == 'F':
        fraud_to_fraud2 += 1
    elif status1 == 'NF' and status2 == 'NF':
        nonfraud_to_nonfraud2 += 1
    else:
        fraud_to_nonfraud2 += 1

print("\n--- Analisis Koneksi ---")
print(f"Fraud-Fraud: {fraud_to_fraud2}")
print(f"Fraud-NonFraud: {fraud_to_nonfraud2}")
print(f"NonFraud-NonFraud: {nonfraud_to_nonfraud2}")

# Deteksi komunitas
print("\n--- Deteksi Komunitas ---")
communities = list(nx.community.greedy_modularity_communities(graph2))
print(f"Jumlah Komunitas: {len(communities)}")
for i, comm in enumerate(communities, 1):
    fraud_nodes = sum(1 for n in comm if graph2.nodes[n]['status'] == 'F')
    print(f"Komunitas {i}: {len(comm)} nodes, {fraud_nodes} fraud nodes")

# VISUALISASI

fig, axes = plt.subplots(1, 2, figsize=(18, 8))

# Visualisasi Latihan 1
pos1 = nx.spring_layout(graph1, seed=42, k=2)
colors1 = ['red' if graph1.nodes[n]['status'] == 'F' else 'green' for n in graph1.nodes()]

nx.draw_networkx_nodes(graph1, pos1, node_color=colors1, node_size=800,
                       alpha=0.9, ax=axes[0], edgecolors='black', linewidths=2)
nx.draw_networkx_edges(graph1, pos1, width=2, alpha=0.6, ax=axes[0])
nx.draw_networkx_labels(graph1, pos1, font_size=12, font_weight='bold', ax=axes[0])
axes[0].set_title('Latihan 1 - Fraud Network\n(Red=Fraud, Green=Non-Fraud)', fontsize=14, fontweight='bold')
axes[0].axis('off')

# Visualisasi Latihan 2
pos2 = nx.spring_layout(graph2, seed=42, k=2)
colors2 = ['red' if graph2.nodes[n]['status'] == 'F' else 'green' for n in graph2.nodes()]

nx.draw_networkx_nodes(graph2, pos2, node_color=colors2, node_size=800,
                       alpha=0.9, ax=axes[1], edgecolors='black', linewidths=2)
nx.draw_networkx_edges(graph2, pos2, width=2, alpha=0.6, ax=axes[1])
nx.draw_networkx_labels(graph2, pos2, font_size=12, font_weight='bold', ax=axes[1])
axes[1].set_title('Latihan 2 - Fraud Network\n(Red=Fraud, Green=Non-Fraud)', fontsize=14, fontweight='bold')
axes[1].axis('off')

plt.tight_layout()
plt.show()


# ANALISIS RISK SCORE

print("\n" + "=" * 50)
print("RISK SCORE ANALYSIS")
print("=" * 50)

def compute_risk_score(graph, node):
    """Hitung risk score berdasarkan jumlah tetangga fraud"""
    neighbors = list(graph.neighbors(node))
    if not neighbors:
        return 0
    fraud_neighbors = sum(1 for n in neighbors if graph.nodes[n]['status'] == 'F')
    return fraud_neighbors / len(neighbors)

print("\n--- Latihan 1: Risk Scores ---")
risk_scores_1 = {node: compute_risk_score(graph1, node) for node in graph1.nodes()}
for node, score in risk_scores_1.items():
    print(f"Node {node} ({node_labels_1[node]}): Risk Score = {score:.2f}")

print("\n--- Latihan 2: Risk Scores ---")
risk_scores_2 = {node: compute_risk_score(graph2, node) for node in graph2.nodes()}
for node, score in risk_scores_2.items():
    print(f"Node {node} ({node_labels_2[node]}): Risk Score = {score:.2f}")

print("\n" + "=" * 50)
print("ANALISIS SELESAI")
print("=" * 50)
