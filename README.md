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

# ER Diagram - Course, Faculty, Student

```mermaid
flowchart LR

    COURSE[COURSE]
    FACULTY[FACULTY]
    STUDENT[STUDENT]

    TEACHES{teaches}
    ENROLLS{enrolled in}

    FACULTY ---|1| TEACHES
    TEACHES ---|N| COURSE

    STUDENT ---|N| ENROLLS
    ENROLLS ---|N| COURSE

    %% COURSE attributes
    COURSE --- c_id((c_id))
    COURSE --- name((name))
    COURSE --- sem((sem))
    COURSE --- year((year))
    COURSE --- FacultyId((FacultyId))

    %% FACULTY attributes
    FACULTY --- fid((fid))
    FACULTY --- name((name))
    FACULTY --- salary((salary))
    FACULTY --- dept((dept))
    FACULTY --- dependent((dependent))

    %% STUDENT attributes
    STUDENT --- sid((s_id))
    STUDENT --- sname((s_name))
    STUDENT --- dept((dept))
    STUDENT --- sem((sem))
    STUDENT --- year((year))
    STUDENT --- gradepoint((gradepoint))
    STUDENT --- grade((grade))
```

---

## 📌 Cardinality Explanation

* **FACULTY (1) — teaches — (N) COURSE**
  → One faculty can teach multiple courses

* **STUDENT (N) — enrolled in — (N) COURSE**
  → Many students can enroll in many courses (**M:N relationship**)

---

## ✅ Notes

* Diamonds = relationships
* Ovals = attributes
* Lines = proper ER connections
* This matches your handwritten diagram closely

---



