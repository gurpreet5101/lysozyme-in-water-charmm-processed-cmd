# lysozyme-in-water-charmm-processed-cmd

MINIMIZATION
gmx grompp -f step4.0_minimization.mdp -c step3_input.gro -r step3_input.gro -p topol.top -n index.ndx -o em.tpr
gmx mdrun -v -deffnm em -nb gpu

EQUILIBRATION
gmx grompp -f step4.1_equilibration.mdp -c em.gro -r em.gro -p topol.top -n index.ndx -o nvt.tpr
gmx mdrun -v -deffnm nvt -nb gpu

PRODUCTION RUN
gmx grompp -f step5_production.mdp -c nvt.gro -t nvt.cpt -p topol.top -n index.ndx -o md.tpr
gmx mdrun -v -deffnm md -nb gpu
