if $U_{CNOT}$ is self adjoint ($U_{CNOT}^2 = I$), then the time dependent control pulse also has to be

$U_{CNOT} = \tau \exp \{ -i \int_0^T H(t) dt \} = U_N U_{N-1}...U_{1}$
Then, to be self adjoint $$U_N U_1=I, ... U_{k+1}U_{N-k} =I$$Thus
$$\exp\{-i H(t_k) \Delta t\} \exp\{-i H(t_{N-k})\Delta t\} =I $$
which imposes more restrictions on the optimization protocol
