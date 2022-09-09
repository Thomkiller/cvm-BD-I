
SELECT * FROM departement;
SELECT * FROM employe;

SELECT employe.prenom, employe.nom, departement.nom 
FROM employe
LEFT JOIN departement
ON employe.departement = departement.id

SELECT employe.prenom, employe.nom, departement.nom 
FROM employe
LEFT JOIN departement
ON employe.departement = departement.id

---11.2-----
SELECT employe.prenom||' '||employe.nom as nom_complet, employe.nas, employe.ville as ville_residence, departement.ville as ville_travail 
FROM employe
left join departement
on employe.departement = departement.id
-----11.4-----
SELECT *
FROM departement, employe
WHERE  departement.id= employe.departement
----11.6------
SELECT employe.prenom||' '||employe.nom as nom_employe, departement.ville
FROM employe
left join departement
on employe.departement = departement.id
Where departement.ville <> 'Montréal'  

----11.8-----
SELECT emp.prenom||' '||emp.nom AS nom_employe,
sup.prenom||' '||sup.nom AS nom_superviseur,
dep_sup.nom
FROM employe AS emp
LEFT JOIN employe AS sup
ON emp.superviseur = sup.nas
LEFT JOIN departement AS dep_emp
on emp.departement = dep_emp.id
LEFT JOIN departement AS dep_sup
on sup.departement = dep_sup.id
WHERE emp.departement = sup.departement


-----11.10-------
SELECT emp1.prenom||' '||emp1.nom||' fait '||emp1.salaire-emp2.salaire||' de plus que '||emp2.prenom||' '||emp2.nom
FROM employe as emp1
INNER JOIN employe as emp2
ON emp2.salaire < emp1.salaire
ORDER BY emp1.salaire-emp2.salaire DESC


-----11.12-------



SELECT sup.prenom||' '||sup.nom, COUNT(sup.nas = emp.superviseur) as decompte
FROM employe as sup
LEFT JOIN employe as emp
ON sup.nas = emp.superviseur
GROUP BY sup.nom, sup.prenom
ORDER BY decompte ASC, sup.nom ASC, sup.prenom ASC
