Note
==================================
 npm install -g pm2@latest
 pm2 start app.js
 pm2 stop 2065
 pm2 restart 2065
 pm2 reload 2065
 pm2 delete all
 
Cluster Mode
==================================
One of the most powerful features of PM2 is the ability to run in cluster mode. This will run Node processes across all available CPUs. This greatly increases your application's ability to handle traffic without having to change any code.
Running multiple Node processes across all the available CPUs acts like a load balancer. So, as long as you are using a server with more than one CPU available, then you are increasing the reliability.
pm2 start app.js -i max
pm2 monit
curl -s "http://localhost:3000?[1-1000]"
 pm2 logs
 pm2 ecosystem simple
 
 module.exports = {
  apps : [{
    name        : "pm2-example-app",
    script      : "./app.js",
    watch       : true,
    instances   : 4,
    exec_mode   : "cluster",
    env: {
      "PORT": 3000,
      "NODE_ENV": "development"
    },
    env_staging : {
      "PORT": 80,
      "NODE_ENV": "staging"
    },
    env_production : {
      "PORT": 80,
      "NODE_ENV": "production"
    }
  }]
}


$ pm2 start ecosystem.config.js --env staging
$ pm2 start ecosystem.config.js --env production

======================================================
Refer Links
======================================================
https://dzone.com/articles/advanced-nodejs-process-management-with-pm2
https://pm2.keymetrics.io/docs/usage/application-declaration/
