# SPECIFICHE TECNICHE – Dashboard Stime Effort

## OBIETTIVO
Realizzare una web app interna che permetta di creare, modificare e visualizzare stime di effort (in ore e costi) per progetti web. Ogni progetto è suddiviso in moduli funzionali a cui viene assegnato un effort stimato e un costo orario.

## STACK TECNOLOGICO
- [ ] Linguaggio: JavaScript / TypeScript (opzionale)
- [ ] Frontend: React (con Vite o CRA)
- [ ] Stile: TailwindCSS
- [ ] Gestione stato: Context API o Zustand
- [ ] Persistenza (fase 1): localStorage
- [ ] Persistenza (fase 2 - [ ] avanzata): Firebase o Supabase
- [ ] Bonus: generazione PDF (es. con jspdf o html2pdf.js)

## STRUTTURA DATI
**Developer:**
```ts
type Developer = {
  id: string;
  name: string;
};
```

**Modulo:**
```ts
type Module = {
  id: string;
  name: string;
  description: string;
  estimatedHours: number;
  hourlyRate: number;
  assignedTo: Developer | null;
};
```

**Progetto:**
```ts
type Project = {
  id: string;
  name: string;
  client: string;
  startDate: string;
  status: "preventivo" | "approvato" | "in_corso" | "chiuso";
  modules: Module[];
};
```
## NAVIGAZIONE DELL’APP
- [ ] `/` → Home (Lista progetti)
- [ ] `/project/:id` → Dettaglio progetto
- [ ] `/new` → Crea nuovo progetto

## FUNZIONALITÀ
**Home / Lista Progetti:**
- [ ] Visualizza progetti in una tabella
- [ ] Colonne: Nome, Cliente, Stato, Data Inizio, Ore Totali, Costo Totale
- [ ] Pulsante "Nuovo Progetto"
- [ ] Click su progetto → dettaglio

**Dettaglio Progetto:**
- [ ] Visualizza informazioni generali
- [ ] Lista dei moduli stimati
- [ ] Totale ore e costo (sommatoria dei moduli)
- [ ] Pulsante per aggiungere/modificare modulo
- [ ] Pulsante “Esporta in PDF” (bonus)

**Nuovo Progetto / Modifica Progetto:**
- [ ] Form con campi: Nome progetto, Cliente, Data inizio, Stato, Lista moduli

**Gestione Moduli:**
- [ ] Nome modulo, Descrizione, Ore stimate, Costo orario, Assegnato a

## CALCOLI AUTOMATICI
- [ ] Totale ore per progetto = somma estimatedHours di ogni modulo
- [ ] Totale costo = somma estimatedHours * hourlyRate

## STORAGE LOCALE (fase 1)
- [ ] Salvare i progetti in localStorage
- [ ] In fase di editing caricare e aggiornare i dati
- [ ] Opzionalmente usare uuid per ID univoci

## BONUS (extra avanzati)
- [ ] Aggiunta supporto effort effettivo
- [ ] Deviazione stima vs reale
- [ ] Filtri sulla home
- [ ] Esportazione PDF preventivo
- [ ] Autenticazione

## UX/UI
- [ ] Layout responsive
- [ ] Interfaccia chiara e ordinata
- [ ] Usare componenti come Card, Badge, Table
- [ ] Pulsanti evidenti

## ESECUZIONE CONSIGLIATA
1. Setup progetto e layout base
2. Implementare salvataggio progetto + moduli
3. Visualizzazione lista progetti
4. Gestione stato via Context/Zustand
5. Calcoli automatici
6. Styling UI
7. Bonus (PDF, backend, autenticazione)

## ORGANIZZAZIONE FILE SUGGERITA
```bash
/src
 ├── components/
 ├── pages/
 ├── context/ (o zustand/)
 ├── utils/
 └── data/ (mock sviluppatori)
 ```

## OBIETTIVI DI APPRENDIMENTO PER LO STAGISTA
- [ ] Gestione di un'app React con più viste e stato condiviso
- [ ] Non ho un gruppo con componenti riutilizzabili
- [ ] Calcoli dinamici e UI reattiva
- [ ] Organizzazione del codice in moduli scalabili
- [ ] Uso di localStorage o database remoto
