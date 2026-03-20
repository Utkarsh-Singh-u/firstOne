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
    STUDENT --- address((address))
    STUDENT --- contact((contact))
    STUDENT --- email((email))

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
    CAR --- type((type))
    CAR --- price((price))
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


