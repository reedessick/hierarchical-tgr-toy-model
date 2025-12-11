Workflow should go something like:

```
for MODE in scaled_normal scaled_exp_abs scaled_ex scaled_normal_q
do
    ./generate 1000 catalog_${MODE}.hdf -v
    ./infer catalog_${MODE}.hdf samples_${MODE}.hdf -v
done
```

**NOTE**, we may also set up p-p test to demonstrate propper coverage?

---

Examples:

```math
\delta\phi
```

catalog_scaled_ex.png
catalog_scaled_exp_abs.png
catalog_scaled_normal_q.png
catalog_scaled_normal.png
samples_scaled_ex.png
samples_scaled_exp_abs.png
samples_scaled_normal_q.png
samples_scaled_normal.png
