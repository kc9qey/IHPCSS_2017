

NXSIZE=101
NYSIZE=641
NP=2

# NZSIZE = NP*NZSLICE
NZSLICE=64

#FC=pgfortran -Mmpi=mpich2 -V11.8
FC=mpif90
OPT=-fast 
MPOPT=-mp -Minfo
OACC=-acc=verystrict -Minfo=accel
ACC=-ta=nvidia,nocache -Minfo=accel
EXES= cpu.out gpu1a.out gpu2a.out gpu3a.out gpu4a.out gpu5a.out gpu1o.out gpu2o.out gpu3o.out gpu4o.out gpu5o.out 

all:  $(EXES)


cpu.out: seismic_CPML_3D_isotropic_MPI_OpenMP.F90
	$(FC) $(OPT) $(MPOPT) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_OpenMP.F90 -o cpu.out  >& buildcpu.log

gpu1a.out: seismic_CPML_3D_isotropic_MPI_ACC_1.F90
	$(FC) $(OPT) $(ACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_ACC_1.F90 -o gpu1a.out  >& buildgpu1a.log

gpu2a.out: seismic_CPML_3D_isotropic_MPI_ACC_2.F90
	$(FC) $(OPT) $(ACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_ACC_2.F90 -o gpu2a.out  >& buildgpu2a.log

gpu3a.out: seismic_CPML_3D_isotropic_MPI_ACC_3.F90
	$(FC) $(OPT) $(ACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_ACC_3.F90 -o gpu3a.out  >& buildgpu3a.log

gpu4a.out: seismic_CPML_3D_isotropic_MPI_ACC_4.F90
	$(FC) $(OPT) $(ACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_ACC_4.F90 -o gpu4a.out  >& buildgpu4a.log

gpu5a.out: seismic_CPML_3D_isotropic_MPI_ACC_5.F90
	$(FC) $(OPT) $(ACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_ACC_5.F90 -o gpu5a.out  >& buildgpu5a.log

gpu1o.out: seismic_CPML_3D_isotropic_MPI_OACC_1.F90
	$(FC) $(OPT) $(OACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_OACC_1.F90 -o gpu1o.out  >& buildgpu1o.log

gpu2o.out: seismic_CPML_3D_isotropic_MPI_OACC_2.F90
	$(FC) $(OPT) $(OACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_OACC_2.F90 -o gpu2o.out  >& buildgpu2o.log

gpu3o.out: seismic_CPML_3D_isotropic_MPI_OACC_3.F90
	$(FC) $(OPT) $(OACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_OACC_3.F90 -o gpu3o.out  >& buildgpu3o.log

gpu4o.out: seismic_CPML_3D_isotropic_MPI_OACC_4.F90
	$(FC) $(OPT) $(OACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_OACC_4.F90 -o gpu4o.out  >& buildgpu4o.log

gpu5o.out: seismic_CPML_3D_isotropic_MPI_OACC_5.F90
	$(FC) $(OPT) $(OACC) -DNXSIZE=$(NXSIZE) -DNYSIZE=$(NYSIZE) -DNZSLICE=$(NZSLICE) -DNUM_PROCS=$(NP) seismic_CPML_3D_isotropic_MPI_OACC_5.F90 -o gpu5o.out  >& buildgpu5o.log

run_cpu:
	mpirun -np $(NP) run_omp.csh cpu.out

run_gpu3a:
	mpirun -np $(NP) run.csh gpu3a.out

run_gpu4a:
	mpirun -np $(NP) run.csh gpu4a.out

run_gpu5a:
	mpirun -np $(NP) run.csh gpu5a.out

run_gpu3o:
	mpirun -np $(NP) run.csh gpu3o.out

run_gpu4o:
	mpirun -np $(NP) run.csh gpu4o.out

run_gpu5o:
	mpirun -np $(NP) run.csh gpu5o.out


clean:
	rm -f *.pnm *.dat *.o $(EXES) *.log plot* timestamp* cuprof*
