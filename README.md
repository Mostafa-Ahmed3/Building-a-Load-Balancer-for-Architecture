<p><span class="fr-close-ol">1. Creating a VPC (Virtual Private Cloud):</span></p>
<ul style="list-style-type: disc;">
    <li>Go to the VPC Dashboard in the AWS Management Console.</li>
    <li>Click on &quot;Your VPCs&quot; in the left-hand navigation pane.</li>
    <li>Click on &quot;Create VPC&quot; and configure the VPC with the appropriate IPv4 block (e.g., 10.0.0.0/16) and create four subnets within this VPC (e.g., 10.0.0.0/24 and 10.0.2.0/24 for the public subnets and 10.0.1.0/24 and 10.0.3.0/24 for the private subnets).</li>
</ul>
<p>2. Setting Up Internet Gateway and Route Tables:</p>
<ul style="margin-bottom:0in;margin-top:0in;" type="disc">
    <li style='margin:0in;font-size:12.0pt;font-family:"Times New Roman",serif;'>Create an internet gateway and attach it to your VPC to enable internet access for resources within the VPC.</li>
    <li style='margin:0in;font-size:12.0pt;font-family:"Times New Roman",serif;'>Create route tables and associate them with the subnets. Ensure that the public subnet has a route to the internet gateway to allow outbound internet access for resources in that subnet.</li>
</ul>
<p>3. Configure Security Groups</p>
<ul style="list-style-type: disc;">
    <li>Create 2 Security Groups for your DB, EC2 instance and Application load balancer.</li>
    <li>Define rules according to the needs.</li>
</ul>
<p>4. Creating EC2 Instance and an AMI for Auto Scaling:</p>
<ul style="margin-bottom:0in;margin-top:0in;" type="disc">
    <li style='margin:0in;font-size:12.0pt;font-family:"Times New Roman",serif;'>Launch EC2 instance with the name Web Server 1.</li>
    <li style='margin:0in;font-size:12.0pt;font-family:"Times New Roman",serif;'>Go to the EC2 Dashboard and click &quot;Launch Instance.&quot;</li>
    <li style='margin:0in;font-size:12.0pt;font-family:"Times New Roman",serif;'>Choose the desired Amazon Machine Image (AMI) for your instances, and select the appropriate instance type and configuration.</li>
</ul>
<ul style="list-style-type: disc;">
    <li>Wait until the Status Checks for Web Server 1 displays 2/2 checks passed.</li>
    <li>Select Web Server 1.</li>
    <li>In the Actions menu, choose Image and templates &gt; Create image, then configure:</li>
</ul>
<p style='margin:0in;font-size:12.0pt;font-family:"Times New Roman",serif;margin-left:.5in;text-indent:.5in;'>Image name: WebServerAMI.</p>
<p style='margin-top:0in;margin-right:0in;margin-bottom:0in;margin-left:.5in;font-size:12.0pt;font-family:"Times New Roman",serif;text-indent:.5in;'>Image description: Lab AMI for Web Server.</p>
<ul style="list-style-type: disc;">
    <li>Choose Create image.</li>
    <li>Use &quot;Launch Template&quot; to define the specifications for the instances.</li>
    <li>In &quot;Auto Scaling Groups&quot;, create a new group, select your launch template/configuration, set the desired, minimum, and maximum number of instances, and select the subnets in multiple AZs.</li>
</ul>
<p>5. Creating RDS DB</p>
<ul style="list-style-type: disc;">
    <li>Navigate to RDS Dashboard.</li>
    <li>Choose to create a new database and select the engine.</li>
    <li>Opt for a &apos;Multi-AZ&apos; deployment to automatically create a synchronous standby replica in a different AZ.</li>
</ul>
<p style='margin:0in;font-size:12.0pt;font-family:"Times New Roman",serif;'>&nbsp;</p>
<p style='margin:0in;font-size:12.0pt;font-family:"Times New Roman",serif;'>The complete architecture you deployed is:</p>
<img src="Diagram.png" alt="Diagarm">
