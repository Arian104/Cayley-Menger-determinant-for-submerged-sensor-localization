# Cayley-Menger Determinant for Submerged Sensor Localization

## Which Method We Have Chosen for Localization?

For this study, we have chosen a **range-based method** utilizing the **Cayley-Menger determinant**. This approach provides a **closed-form solution** for submerged sensor localization by leveraging **pairwise distance measurements** to determine sensor positions geometrically. It is computationally efficient and robust, making it well-suited for underwater environments where precision and reliability are critical.

## Why Use CMD?

- CMD eliminates iterative solutions and computational overhead from optimization-based methods.
- It works well with small-scale networks where accurate distance measurements are available.
- It handles multi-dimensional localization (2D and 3D) using algebraic expressions.
- The volume of the tetrahedron is computed using the **Cayley-Menger determinant**, which provides a means to derive the volume of a simplex based on the squared distances between its vertices.

---

## Localization Model Using Surface Beacons

To effectively **localize and rescue** a submerged sensor, the sensor must be capable of receiving and transmitting **acoustic signals**. Based on an estimated area where the sensor is likely located, a rescue ship is dispatched to that region. 

To improve localization accuracy, two additional submerged sensors are deployed underwater, forming a **tetrahedron** with the original sensor. This geometric configuration enables precise **triangulation**, significantly enhancing the likelihood of successfully locating and retrieving the submerged sensor.

---

## Localization Model Using Surface Beacons (Alternative Configuration)

This model can be implemented using either a **single surface ship** or **multiple beacons**:

- If using **one beacon**, it must be moved to six different locations to solve the **Cayley-Menger determinant**, assuming the lost submerged sensor is static.
- However, in reality, the sensor is moving. A more effective approach is to deploy **five surface beacons** from the main ship.
- These beacons are placed at specific distances, forming a **pentagon shape** around the main ship. This ensures that the beacons receive signals with only **millisecond delays**, allowing for real-time tracking.
- The **pentagon shape prevents singularity matrix errors** that could occur if data were collected along a straight line, ensuring more accurate localization of the submerged sensor.

---

## Generating a Realistic Acoustic Signal Communication Dataset

Since there is **no publicly available dataset** for acoustic signal communication, we are generating our own dataset to solve the Cayley-Menger determinant.

1. We used a **random function** to generate **100 different locations** for the main ship and adjusted the distances to the other surface beacons accordingly.
2. We then used the **Euclidean distance** to determine the values from the surface beacons to the submerged beacons. To make the dataset more realistic, **Gaussian error** was added to the measurements.

---

## Implementing the Cayley-Menger Determinant

- After loading the distances, the code employs the **Cayley-Menger determinant**, a mathematical technique tackling a complex geometry problem.
- It determines the unknown distances between underwater sensors using the known distances between surface beacons and submerged sensors.

After determining the unknown distances, the code calculates the **final coordinates** of the submerged sensors in a **2D plane**. Using geometric formulas based on the distances between sensor pairs, it computes the **x and y coordinates** of each sensor relative to the first sensor.

These coordinates are then **stored and saved** as the output for each iteration, enabling the determination of sensor positions from the acoustic signal data.

---

## Graphical Representation of Distance Errors in 100 Iterations

From the graphs, we can observe the **distance error** between submerged sensor pairs. The error is minimal, and when considering the lost sensor as a **submarine**, its vast size makes the distance error negligible. Over **100 iterations**, the maximum error recorded is only **0.5**.

---

## Graphical Representation of Mean Errors in 100 Iterations

In these figures, we can see the **mean error represented as a line**, while the error of each iteration is shown as **dots**. 

- The figures represent sensors **S2 and S3**.
- The mean error for **S2 is 0.11**, while for **S3 it is 0.17**.
- These errors are **negligible** when considering the size of the lost ship or vehicle.

---

