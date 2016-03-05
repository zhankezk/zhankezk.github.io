--- 
layout: post
title: "Multi-Site solution deployments in Azure"
author: "Ke"
comments: true
---

* When having multiple web projects in a solution, Azure by default only deploy the first alphabetically project regardless your settings. Source: [Stackoverflow](http://stackoverflow.com/questions/22021102/cant-deploy-correct-website-from-multi-project-solution-using-git-deployment-to) & [MSDN](http://social.msdn.microsoft.com/forums/azure/en-US/95f161f6-9370-43ad-9ac5-714f8978cc5e/continuous-integration-deploying-wrong-project-from-solution?forum=azuregit)

* Key: Project

  Value: webui/webui.csproj

  Key: SCMBUILDARGS

  Value: -p:Configuration=Debug

  This tells Azure to deploy this project and this configuration when using git and bitbucket ... Not visual studio online, which should be from build definition.