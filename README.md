# Practice-lab-1-answer-
Practical Lab 1: Google Colab Setup & Building a Knowledge-Based System (KBS)

Course: Artificial Intelligence
Program: BSCS – 4th Semester

---

Exercise 1: Degree Honors Rule

Objective: Add a new rule to the Knowledge Base for students completing their degree program.

Python Code:

# Exercise 1: Degree Honors Rule

honors_rule = {
    "id": "RULE_07",
    "conditions": {
        "cgpa_min": 3.70,
        "disciplinary_warnings": 0
    },
    "condition_type": "degree_honors",
    "status": "Graduated with Magna Cum Laude Honors",
    "action": "Eligible for degree honors."
}

UNIVERSITY_KB["rules"].append(honors_rule)

print("New Degree Honors Rule Added Successfully!")

Explanation:

This rule checks whether a student has a CGPA of 3.70 or above and has no disciplinary warnings. If both conditions are satisfied, the student qualifies for Magna Cum Laude Honors.

---

Exercise 2: Tracing Forward Chaining

Objective: Modify the "evaluate_student()" function to display each evaluated rule during the inference process.

Python Code:

# Exercise 2: Forward Chaining

def evaluate_student(student_record, kb):

    print("\nEvaluating Student:", student_record["student_name"])

    print("Checking Attendance Rule...")

    if student_record["attendance"] < 75:
        print("Attendance Rule Matched!")

        return {
            "grade": "F",
            "status": "Debarred",
            "action": "Ineligible to sit for final exam."
        }

    print("Attendance Rule Not Matched.")

    marks = student_record["total_marks"]

    for rule in kb["rules"]:

        if rule["condition_type"] == "marks_range":

            print("Checking:", rule["id"])

            if rule["conditions"]["marks_min"] <= marks <= rule["conditions"]["marks_max"]:

                print("Rule Matched:", rule["id"])

                return {
                    "grade": rule["grade"],
                    "status": rule["status"],
                    "action": rule["action"]
                }

    return {
        "grade": "N/A",
        "status": "Invalid Score Entry",
        "action": "Verify submitted marks."
    }

Explanation:

Forward chaining is a reasoning technique that starts with available facts and checks rules to reach a conclusion. This modified function displays each evaluated rule and identifies the rule that matches the student's information.

---

Conclusion

In this practical lab, we implemented two additional features in a Knowledge-Based System:

1. Added a Degree Honors Rule using Python dictionaries.
2. Implemented Forward Chaining with step-by-step rule tracing.

These exercises demonstrate how a rule-based expert system evaluates conditions and produces decisions using an inference engine.
