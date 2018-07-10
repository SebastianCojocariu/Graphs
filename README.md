Sebastian Cojocariu 321CB UPB ACS										                  
                                      
                                      Graphs
1)Minlexbfs
	Pentru a obtine parcurgerea minima lexicografica vom folosi urmatorul
artificiu:vom sorta nodurile din fiecare lista de adiacenta a fiecarui nod
crescator,dupa care vom apela efectiv bfs incepand din nodul cel mai mic
(in cazul nostru 1). 
	Complexitate temporala: BFS=>O(|V|+|E|)<=O(|V|+|V|^2)=O(|V|^2),iar fiecare 
sortare poate sa aiba maxim O(|V|*log(|V|))=>Theta(|V|^2*log(|V|) 
(cel mai defavorabil caz este atunci cand graful este complet)=>Complexitate 
temporala:Theta(|V|^2*log(|V|)
	Complexitate spatiala : O(V)(listele de adiacenta).


2)Disjcnt
	Pentru ca 2 noduri sa nu aiba 2 drumuri disjuncte intre ele e necesar ca 
macar o muchie sa apara in toate drumurile ce le leaga.Asadar,daca scoatem orice 
astfel de muchie deconectam graful,deci acea muchie e muchie critica.
	Ideea de baza consta in a folosi algoritmul lui Tarjan pentru a determina
muchiile critice din graf.Intrucat pot exista muchii duplicate,la acest algoritm,
pe langa verificare conditiei uzuale de muchie critica,
mai verificam si ca muchia sa apara fix o singura data in graf.Stergem apoi aceste
muchii critice.Cu un dfs aflam numarul de componente conexe,iar int interiorul fiecarei
componente conexa stim acum ca exista 2 drumuri disjuncte intre oricare 2 noduri.
Daca avem x noduri in componenta=>x*(x-1)/2 perechi ordonate pe care le adaugam la 
suma globala.
	Complexitate temporala: Tarjan=>O(|V|+|E|) + DFS=>O(|V|+|E|) + stergerea
muchiilor(Theta(nr_muchii_critice *E) <= Theta(|E|^2),cu toate ca vor fi cu mult mai putine)
deci complexitatea va fi O(|V|+|E|).(sau Theta(E^2) daca sa zicem avem un graf 
sub forma de "linie",in care toate muchiile mai putin prima si ultima sunt critice.)
	Complexitate spatiala : O(V)(listele de adiacenta).	

4)Revedges
	Ideea centrala consta in marca costul fiecarei muchii a grafului initial cu 0,
si adaugarea muchiilor opuse pentru fiecare muchie existenta in graf(acestea vor avea
acum cost 1).Numarul minim de muchii pentru care trebuie sa le schimbam sensul pentru a ajunge
de la i la j este egal cu drumul minim de la i la j in graful nou construit.Intrucat
ni se vor cere mai multe Queries,vom folosi algoritmul FloydWharshall pentru a determina distanta
minima intre oricare 2 noduri din graf.
	Complexitate temporala: O(|V|^3) (FloydWarshall).
	Complexitate spatiala : O(|V|^2) (matricea de la FloydFharsall) + O(|V|^2)(graful initial
reprezentat ca matrice de adiacenta)=> O(|V|^2).	
