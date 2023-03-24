The challenge provides only one file to work with:
quantum_artifact.qasm - OPENQASM 2.0 file as stated in the first line

Googling I have found that it can be opened in Jupyter Notebook (1) or IBMQ device (2).

If you use your own notebook, first install qiskit by running
pip3 install qiskit

Then start a new notebook and use the code provided in the solution here.

1. Import Qiskit
2. Load the quantum cirquit (3)
3. Run the simulation of the cirquit (4)
4. Convert resulting binary to ASCII


(1) https://quantumcomputing.stackexchange.com/questions/21717/qasm-files-on-jupyter-notebook
(2) https://quantumcomputing.stackexchange.com/questions/9695/how-to-run-a-qasm-file-on-ibmq-device
(3) https://qiskit.org/documentation/stubs/qiskit.circuit.QuantumCircuit.from_qasm_file.html
(4) https://www.youtube.com/watch?v=VzNk-nvAbqw
