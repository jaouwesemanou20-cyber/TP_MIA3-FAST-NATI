#include <iostream>
#include <string>
#include <vector>
#include <iomanip>

using namespace std;

// ==========================================
// CLASSE ETUDIANT
// ==========================================

class Etudiant
{
private:
    string matricule;
    string nom;
    string prenom;

public:
    Etudiant(string m, string n, string p)
    {
        matricule = m;
        nom = n;
        prenom = p;
    }

    string getMatricule() const
    {
        return matricule;
    }

    string getNom() const
    {
        return nom;
    }

    string getPrenom() const
    {
        return prenom;
    }

    void afficher() const
    {
        cout << "Matricule : " << matricule << endl;
        cout << "Nom : " << nom << endl;
        cout << "Prenom : " << prenom << endl;
    }
};

// ==========================================
// CLASSE CHAMBRE
// ==========================================

class Chambre
{
private:
    int numero;
    int capacite;
    vector<string> occupants;

public:
    Chambre(int num, int cap)
    {
        numero = num;
        capacite = cap;
    }

    int getNumero() const
    {
        return numero;
    }

    int getCapacite() const
    {
        return capacite;
    }

    int getPlacesOccupees() const
    {
        return occupants.size();
    }

    int getPlacesLibres() const
    {
        return capacite - occupants.size();
    }

    bool estDisponible() const
    {
        return occupants.size() < capacite;
    }

    bool contientEtudiant(string matricule) const
    {
        for (const string& m : occupants)
        {
            if (m == matricule)
                return true;
        }

        return false;
    }

    bool ajouterOccupant(string matricule)
    {
        if (!estDisponible() || contientEtudiant(matricule))
            return false;

        occupants.push_back(matricule);
        return true;
    }

    bool retirerOccupant(string matricule)
    {
        for (size_t i = 0; i < occupants.size(); i++)
        {
            if (occupants[i] == matricule)
            {
                occupants.erase(occupants.begin() + i);
                return true;
            }
        }

        return false;
    }

    void afficher() const
    {
        cout << "Chambre numero : " << numero << endl;
        cout << "Capacite : " << capacite << endl;
        cout << "Places occupees : " << occupants.size() << endl;
        cout << "Places libres : " << getPlacesLibres() << endl;

        if (estDisponible())
            cout << "Etat : Disponible" << endl;
        else
            cout << "Etat : Complete" << endl;
    }
};

// ==========================================
// CLASSE DEMANDE
// ==========================================

class Demande
{
private:
    Etudiant etudiant;
    string dateDemande;
    string statut;

public:
    Demande(Etudiant e, string date)
        : etudiant(e)
    {
        dateDemande = date;
        statut = "En attente";
    }

    string getMatricule() const
    {
        return etudiant.getMatricule();
    }

    string getStatut() const
    {
        return statut;
    }

    void accepter()
    {
        statut = "Acceptee";
    }

    void afficher() const
    {
        etudiant.afficher();
        cout << "Date de demande : " << dateDemande << endl;
        cout << "Statut : " << statut << endl;
    }
};

// ==========================================
// CLASSE OCCUPATION : HISTORIQUE
// ==========================================

class Occupation
{
private:
    string matricule;
    int numeroChambre;
    string dateEntree;
    string dateSortie;

public:
    Occupation(string m, int num, string entree)
    {
        matricule = m;
        numeroChambre = num;
        dateEntree = entree;
        dateSortie = "En cours";
    }

    string getMatricule() const
    {
        return matricule;
    }

    bool estEnCours() const
    {
        return dateSortie == "En cours";
    }

    void enregistrerDepart(string date)
    {
        dateSortie = date;
    }

    void afficher() const
    {
        cout << "Matricule : " << matricule << endl;
        cout << "Chambre : " << numeroChambre << endl;
        cout << "Date d'entree : " << dateEntree << endl;
        cout << "Date de sortie : " << dateSortie << endl;
        cout << "--------------------------" << endl;
    }
};

// ==========================================
// CLASSE GESTION RESIDENCE
// ==========================================

class GestionResidence
{
private:
    vector<Etudiant> etudiants;
    vector<Chambre> chambres;
    vector<Demande> demandes;
    vector<Occupation> historique;

public:

    // Enregistrer un etudiant et sa demande

    void enregistrerDemande(Etudiant e, string date)
    {
        string mat = e.getMatricule();

        for (const Etudiant& et : etudiants)
        {
            if (et.getMatricule() == mat)
            {
                cout << "Etudiant deja enregistre." << endl;
                return;
            }
        }

    
