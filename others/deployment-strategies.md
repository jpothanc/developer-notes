# Deployment Strategies

Nothing beats the satisfaction of seeing our code go live to millions of users. It is always thrilling to see. But getting there is not always easy. Let’s explore some of the common strategies.

## Big Bang

One of the earliest methods of deploying changes to production is the Big Bang Deployment. Picture it like ripping off a band-aid. We push all our changes at once. This causes a bit of downtime as we have to shut down the old system to switch on the new one.

The downtime is usually short, but be careful - it can sting if things don't go as planned. Preparation and testing are key. If things go wrong? We roll back to the previous version. Rolling back is not always pain-free. We still might disrupt users and there could be data implications. We need to have a solid rollback plan. Big Bang is sometimes the only choice, for example, when an intricate database upgrade is involved.

## Rolling Deployment

Then we have the Rolling Deployment. It is more like a marathon than a sprint. This method lets us incrementally update different parts of the system over time. It's a staged rollout where we gradually deploy the new version of the application to the production environment.

Here's an example of how it might work. Imagine we have 10 servers running our application. In a rolling deployment, we might take down the first server, deploy the new version of our application there, and bring it back online. Once we've confirmed everything is working as expected, we'll move on to the second server, and so on. This approach allows the new version to gradually replace the old one, server by server, until the entire system is updated. One big advantage of Rolling Deployment is that it usually prevents downtime. While we're updating one server, the others are still up and running, serving our users. Another advantage is that we can spot and mitigate any issues early during the rollout.

This reduces the risk of widespread problems. We're only ever exposing a small part of our system to the new version at any one time. However, rolling deployment is typically a slower process. And while it reduces the risk of system-wide issues, it doesn't entirely eliminate it. If an issue slips past our initial checks, it might still propagate as we update more servers. This strategy doesn't support targeted rollouts. We can't control which users get the new version during the rollout. All users will gradually see the new version as we update the servers. We can't direct the new version to specific users based on criteria like location, device type, etc. Rolling deployment is a popular choice for many teams. It balances risk and user impact in a controlled, methodical way.

## Blue-Green

Now let's take a look at the Blue-Green Deployment. Here, we maintain two identical production environments, cleverly named blue and green. At any given time, one side is active and visible to users, and the other is idle. The active environment (say, blue) serves the current live version of the application to the users. The idle one (green) is our playground where we can safely deploy and test the new version. Here's how it might work. When we have a new version ready to go, we deploy it to the green environment. While this is happening, the blue environment is still live and serving the current version of the application to users. Our QA team then tests the new version in the green environment. This gives us the chance to catch and fix any bugs or issues before they reach our users. Once the new version in the green environment is deemed ready, we simply switch the load balancer to redirect traffic from the blue environment to the green one. Users are seamlessly transitioned to the new version of the application with zero downtime. Now the blue environment becomes idle and serves as our safety net. If we encounter any issues with the new version, we can quickly switch back to the blue environment, effectively rolling back to the previous version. While Blue-Green Deployment allows for seamless transitions and easy rollbacks, there's a catch. Just like with the rolling deployment, we can't direct the new version to specific users. The switch from blue to green happens for all users at once. It is also resource-intensive. Maintaining two identical production environments doubles the infrastructure and resource needs. We could spin down the idle environment between deployments, but this introduces complexity. Managing two parallel production environments and ensuring seamless data synchronization can add significant complexity to the deployment process. It requires sophisticated infrastructure management and tooling. However, with its high level of control and minimized risk, Blue-Green Deployment remains a popular strategy for smooth user experience and reliable rollbacks.

## Canary

Next up is Canary Deployment, named after the age-old practice of using canaries in coal mines to detect dangerous gasses. If the canary was in distress, miners knew it was time to evacuate.

Here's how it goes. Instead of deploying the new version to all servers or users, we choose a small subset, our 'canaries'. It could be a percentage of servers or a group of users, often selected based on certain criteria.

For example, we might start by deploying to a single server, or a small cluster, or even a certain geographical location. This allows us to monitor the performance of the new version under real-world conditions, but on a much smaller scale. If everything goes well and our new version performs as expected, we can gradually roll it out to the rest of the servers or users. But if something goes wrong, we've got a safety net. We can halt the deployment, fix the issues, and try again, all without impacting the majority of our user base. This incremental approach offers us both safety and control. Canary Deployment also gives us the power of targeted rollouts. Unlike Rolling or Blue-Green Deployments, we can direct our canaries based on user-specific criteria, like geographical location or device type. However, Canary Deployment does come with its own set of challenges.

It requires careful monitoring and automated testing for the canaries. It requires somewhat complicated infra tooling to ramp up or halt the deployment as needed.
The strategy can be complex to implement and manage, especially when dealing with database schema changes or API compatibility issues.
Canary Deployment is usually not a standalone strategy. It's often combined with Rolling Deployment to create an approach that brings together the best of both worlds.

## Feature Toggle

Finally, as a bonus strategy, we have Feature Toggle. It stands a bit apart from the other strategies we've discussed. It's not about deploying a new version of the entire application, but rather about managing specific new features within that application. With Feature Toggle, we introduce a 'toggle' or 'switch' in the code for new features. This allows us to turn the feature on or off for certain users or circumstances. Think of it as a gate that we can open or close. It controls who gets to see the new feature. Feature Toggle can be used in combination with any of the deployment strategies we've discussed. Let's say we're doing a Canary Deployment.

We can turn on the feature toggle for just the canary users, letting them test out the new feature while the rest of the user base carries on with
