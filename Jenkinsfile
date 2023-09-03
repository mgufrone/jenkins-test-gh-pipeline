stage("Setup") {
    slackSend(channel: "#notification", message: "<${env.BUILD_URL}|Deployment> request received", attachments: [[
        "text": "Proceed to deploy?",
        "fallback": "You are unable to choose a game",
        "callback_id": "${env.JOB_NAME}:${env.BUILD_NUMBER}",
        "color": "#3AA3E3",
        "attachment_type": "default",
        "actions": [
            [
                "name": "prompt",
                "text": "Abort",
                "type": "button",
                "style": "danger",
                "value": "abort"
            ],
            [
                "name": "prompt",
                "text": "Approve",
                "type": "button",
                "style": "primary",
                "value": "approve"
            ],
        ]
    ]])
    def approval = input(message: "Proceed to deploy?", parameters:[
        string(name: "SLACK_SUBMITTER", defaultValue: "Admin", description: "Submitter")
    ])
    println "approved by ${approval}"
}
