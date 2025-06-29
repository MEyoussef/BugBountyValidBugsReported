Just documenting the valid bugs **me & my friend** reported to Bugcrowd

1- No Rate Limit on Sign-Up Page

Me & my friend were testing a sign-up page and I found that they had absolutely no rate limit for how many accounts you can create. I reported the bug and it was rated as **P4 - Info** as I got **5 points**.

2- Privilege Escalation Leads to Deleting Messages Under Outbound

Me & my friend were testing roles and access control issues, and we found out that if an admin invited a new member for the organization, and as the new member creates a new message under a page called **(Outbound)**, when the new member tries to delete it by marking up the checkbox beside the message and clicking delete, it shows an alert box indicating a lack of permission. But if we access the message you created and click delete, the message gets deleted.
This issue was rated as **P4** and I received **2 points** and my friend received **3 points** with a **\$300 bounty** (\$150 each).

3- Privilege Escalation Leads to Unauthorized Data

Me & my friend were testing roles and access control issues, and we found out that if an admin invites a new member to the organization with limited permissions, and this member tries to access the audience leads page, they normally see a **no permission** error when accessing any lead directly.

But we discovered that if you capture the permission-check request in Burp Suite

`GET /ember/permissions?app_id=XXXXX HTTP/2`

and manually change the endpoint to target a specific lead like

`GET /ember/users/[victim_user_id]?app_id=XXXXX HTTP/2`

and send it, you get **200 OK** and the full sensitive data of that lead, bypassing permissions completely.
