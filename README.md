<ol>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;tab-stops:list .5in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span dir="LTR"></span>Creating a VPC (Virtual Private Cloud):<o:p></o:p></span></li>
</ol>
<ul>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Go to the VPC Dashboard in the AWS Management Console.<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Click on "Your VPCs" in the left-hand navigation pane.<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Click on "Create VPC" and configure the VPC with the appropriate IPv4 block (e.g., 10.0.0.0/16) and create four subnets within this VPC (e.g., 10.0.0.0/24 and 10.0.2.0/24 for the public subnets and 10.0.1.0/24 and 10.0.3.0/24 for the private subnets).<o:p></o:p></span></li>
</ul>
<ol>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;tab-stops:list .25in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span dir="LTR"></span>Setting Up Internet Gateway and Route Tables:<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;tab-stops:list .25in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span dir="LTR"></span>Configure Security Groups<o:p></o:p></span></li>
</ol>
<ul style="list-style-type:disc;margin-bottom:0in;margin-top:0in;" type="disc">
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;">Create an internet gateway and attach it to your VPC to enable internet access for resources within the VPC.<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;">Create route tables and associate them with the subnets. Ensure that the public subnet has a route to the internet gateway to allow outbound internet access for resources in that subnet.<o:p></o:p></span></li>
</ul>
<ul>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Create 2 Security Groups for your DB, EC2 instance and Application load balancer.<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Define rules according to the needs.<o:p></o:p></span></li>
</ul>
<ol>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;tab-stops:list .25in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span dir="LTR"></span>Creating EC2 Instance and an AMI for Auto Scaling:<o:p></o:p></span></li>
</ol>
<ul style="list-style-type:disc;margin-bottom:0in;margin-top:0in;" type="disc">
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;">Launch EC2 instance with the name Web Server 1.<o:p></o:p></span></li>
</ul>
<ul style="list-style-type:disc;margin-bottom:0in;margin-top:0in;" type="disc">
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;">Go to the EC2 Dashboard and click "Launch Instance."<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;">Choose the desired Amazon Machine Image (AMI) for your instances, and select the appropriate instance type and configuration.<o:p></o:p></span></li>
</ul>
<ul>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Wait until the Status Checks for Web Server 1 displays 2/2 checks passed.<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Select Web Server 1.<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>In the Actions menu, choose Image and templates &gt; Create image, then configure:<o:p></o:p></span></li>
</ul>
<p style="line-height:107%;margin:0in 0in 0in .5in;text-indent:.5in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;">Image name: WebServerAMI.<o:p></o:p></span></p>
<p style="line-height:107%;margin:0in 0in 0in 0.5in;text-indent:.5in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;">Image description: Lab AMI for Web Server.<o:p></o:p></span></p>
<ul>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Choose Create image.<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Use "Launch Template" to define the specifications for the instances.&nbsp;<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>In "Auto Scaling Groups", create a new group, select your launch template/configuration, set the desired, minimum, and maximum number of instances, and select the subnets in multiple AZs.<o:p></o:p></span></li>
</ul>
<ol>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;tab-stops:list .25in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span dir="LTR"></span>Creating RDS DB<o:p></o:p></span></li>
</ol>
<ul>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Navigate to RDS Dashboard.<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Choose to create a new database and select the engine.<o:p></o:p></span></li>
    <li style="line-height:107%;margin-bottom:0in;margin-right:0in;margin-top:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"><span style="font-family:Symbol;"></span><span dir="LTR"></span>Opt for a 'Multi-AZ' deployment to automatically create a synchronous standby replica in a different AZ.<o:p></o:p></span></li>
</ul>
<p style="line-height:107%;margin:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;"></span></p>
<p style="line-height:107%;margin:0in;"><span style="font-family:&quot;Times New Roman&quot;, serif;font-size:12pt;">The complete architecture you deployed is:<o:p></o:p></span></p>
<img src="Diagram.png" alt="Diagarm">
