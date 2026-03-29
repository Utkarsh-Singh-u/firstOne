# ER Diagram (Proper ER Notation)

```mermaid
flowchart LR

    EMP[EMP]
    COMP[COMP]

    WORKS_IN{works in}

    EMP --- WORKS_IN
    WORKS_IN --- COMP

    EMP --- e_id((e_id))
    EMP --- e_name((e_name))
    EMP --- salary((salary))
    EMP --- e_city((e_city))

    COMP --- c_id((c_id))
    COMP --- c_name((c_name))
```

# ER Diagrams (With Proper Notation & Cardinality)

---

## 1️⃣ Student – Faculty – Department

```mermaid
flowchart LR

    STUDENT[STUDENT]
    FACULTY[FACULTY]
    DEPT[DEPARTMENT]

    ADVISED_BY{advised by}
    BELONGS_TO{belongs to}

    STUDENT ---|N| ADVISED_BY
    ADVISED_BY ---|1| FACULTY

    STUDENT ---|N| BELONGS_TO
    BELONGS_TO ---|1| DEPT

    STUDENT --- id((id))
    STUDENT --- name((name))
    STUDENT --- sems((sems))
    STUDENT --- enrolled_year((enrolled_year))
    STUDENT --- credit((credit))
    STUDENT --- dept_no((dept_no))
    STUDENT --- facul_id((facul_id))

    FACULTY --- f_id((f_id))
    FACULTY --- f_name((f_name))
    FACULTY --- research((research))

    DEPT --- d_no((d_no))
    DEPT --- d_name((d_name))
    DEPT --- no_students((no_of_students))
```

---

## 2️⃣ Customer – Car

```mermaid
flowchart LR

    CUSTOMER[CUSTOMER]
    CAR[CAR]

    OWNS{owns}

    CUSTOMER ---|1| OWNS
    OWNS ---|N| CAR

    CUSTOMER --- c_id((c_id))
    CUSTOMER --- c_name((c_name))

    CAR --- car_id((car_id))
    CAR --- brand((brand))
    CAR --- cost((type))
    CAR --- ins_amount((price))
```

---

## 3️⃣ Employee – Company

```mermaid
flowchart LR

    EMP[EMPLOYEE]
    COMP[COMPANY]

    WORKS_IN{works in}

    EMP ---|N| WORKS_IN
    WORKS_IN ---|1| COMP

    EMP --- e_id((e_id))
    EMP --- e_name((e_name))
    EMP --- salary((salary))

    COMP --- c_id((c_id))
    COMP --- c_name((c_name))
```

---

## 📌 Cardinality Meaning

* **1** → One
* **N** → Many

### Examples:

* `STUDENT ---|N| ADVISED_BY ---|1| FACULTY`
  → Many students are advised by one faculty

* `CUSTOMER ---|1| OWNS ---|N| CAR`
  → One customer owns many cars

---

## ✅ Notes

* This uses **Mermaid Flowchart** to mimic real ER diagrams
* Diamonds = Relationships
* Ovals = Attributes
* Lines = Proper ER connections (no arrows)

---

# ER Diagram - Clean Layout (Course System)

```mermaid
flowchart TB

    %% Entities
    FACULTY[Faculty]
    COURSE[Course]
    STUDENT[Student]

    %% Relationships
    TEACHES{teaches}
    ENROLLS{enrolled in}

    %% Connections (no crossing)
    FACULTY ---|1| TEACHES
    TEACHES ---|N| COURSE

    STUDENT ---|N| ENROLLS
    ENROLLS ---|N| COURSE

    %% Faculty attributes
    FACULTY --- f_id((f_id))
    FACULTY --- f_name((name))
    FACULTY --- salary((salary))
    FACULTY --- dept((dept))

    %% Course attributes
    COURSE --- c_id((c_id))
    COURSE --- c_name((name))
    COURSE --- sem((sem))
    COURSE --- year((year))

    %% Student attributes
    STUDENT --- s_id((s_id))
    STUDENT --- s_name((name))
    STUDENT --- grade((grade))
    STUDENT --- gradepoint((gradepoint))
```
## 3️⃣ Employee – Company

```mermaid
flowchart LR

    EMP[EMPLOYEE]

    EMP --- id((e_id))
    EMP --- name((e_name))
    EMP --- phno((phno))
    EMP --- salary((salary))

```
```mermaid
---
flowchart TB

    %% Entities
    CUSTOMER[Customer]
    ACCOUNT[Account]
    BRANCH[Branch]
    TRANSACTION[Transaction]

    %% Relationships
    OWNS{owns}
    BELONGS{belongs to}
    HAS_TXN{has transaction}

    %% Connections
    CUSTOMER ---|1| OWNS
    OWNS ---|N| ACCOUNT

    ACCOUNT ---|N| BELONGS
    BELONGS ---|1| BRANCH

    ACCOUNT ---|1| HAS_TXN
    HAS_TXN ---|N| TRANSACTION

    %% Attributes
    CUSTOMER --- c_id((CUSID))
    CUSTOMER --- c_name((CNAME))
    CUSTOMER --- location((LOC))

    ACCOUNT --- a_no((ANO))
    ACCOUNT --- balance((BAL))
    ACCOUNT --- start((SDATE))

    BRANCH --- b_id((BID))
    BRANCH --- b_name((FNAME))

```
