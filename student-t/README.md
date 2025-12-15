Workflow should go something like:

```
NONCENTRAL=5
for DPHI_MODE in \
    scaled_student_t \
    scaled_noncentral_student_t
do
    for M_MODE in M m1
    do

        for NUM_DOF in 3 4 5 10 20 50 100
        do

            ./generate \
                1000 \
                catalog_${DPHI_MODE}-${M_MODE}_${NUM_DOF}_${NONCENTAL}.hdf \
                --dphi-mode ${DPHI_MODE} \
                --num-dof $NUM_DOF \
                --noncentral $NONCENTAL \
                --m-mode ${M_MODE} \
                --seed 1234 \
                -v

            ./infer \
                catalog_${DPHI_MODE}-${M_MODE}_${NUM_DOF}_${NONCENTAL}.hdf \
                samples_${DPHI_MODE}-${M_MODE}_${NUM_DOF}_${NONCENTAL}.hdf \
                --num-warmup   5000 \
                --num-samples 50000 \
                --seed 5678 \
                -v

            ./infer \
                catalog_${DPHI_MODE}-${M_MODE}_${NUM_DOF}_${NONCENTAL}.hdf \
                samples_${DPHI_MODE}-${M_MODE}_${NUM_DOF}_${NONCENTAL}_one_scaling.hdf \
                --one-scaling \
                --num-warmup   5000 \
                --num-samples 50000 \
                --seed 5678 \
                -v

        done
    done
done
```
