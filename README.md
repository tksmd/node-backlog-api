backlog-api
==============================================================================

[Backlog API](http://backlog.jp/api/) wrapper for Node.js

    var backlogApi = require('backlog-api');
    
    var backlog = backlogApi('space', 'user', 'pass');
    
    backlog.findIssue({
      projectId: 1,
      statusId: [1, 2, 3],
    }, function(err, issues) {
      console.log(issues);
    });


Installation
------------------------------------------------------------------------------

    $ npm install backlog-api


Example
------------------------------------------------------------------------------

    // show 'BAPI' project, 'bouzuya' user, 'imcomplete' issues.
    var backlogApi = require('backlog-api');
    
    // set env
    // process.env.BACKLOG_SPACE_ID
    // process.env.BACKLOG_USERNAME
    // process.env.BACKLOG_PASSWORD
    var backlog = backlogApi();
    
    // get project id 
    backlog.getProjects(function(err, projects) {
      if (err) throw err;
      var projectId = projects.filter(function(p) {
        return p.key === 'BAPI';
      })[0].id;
      
      // get user id
      backlog.getUsers({
        projectId: projectId
      }, function(err, users) {
        if (err) throw err;
        var userId = users.filter(function(u) {
          return u.name === 'bouzuya'
        })[0].id;
        
        // get issues
        backlog.findIssue({
          projectId: projectId,
          assignerId: userId,
          statusId: [1, 2, 3]
        }, function(err, issues) {
          console.log(issues);
        });
      });
    });


Todo
------------------------------------------------------------------------------

- createIssue
- updateIssue
- switchStatus
- addComment
- addIssueType
- updateIssueType
- deleteIssueType
- addVersion
- updateVersion
- deleteVersion
- addComponent
- updateComponent
- deleteComponent
- getProjectSummaries
- getUser
- getUserIcon
- getActivityTypes
- getStatuses
- getResolutions
- getPriorities
- getCustomFields
- getChildIssues
- admin.getUsers
- admin.getUser
- admin.updateUser
- admin.deleteUser
- admin.getProjects
- admin.addProject
- admin.updateProject
- admin.deleteProject
- admin.getProjectUsers
- admin.addProjectUser
- admin.updateProjectUsers
- admin.deleteProjectUser
- admin.addCustomField
- admin.updateCustomField
- admin.deleteCustomField

