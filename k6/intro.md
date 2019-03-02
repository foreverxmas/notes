# run local
>k6 run script.js
# run docker
>docker run -i loadimpact/k6 run - < script.js
# run remote and paused
>k6 run --address 1.2.3.4:5678 --paused script.js

