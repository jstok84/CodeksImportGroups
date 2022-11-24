import http.client
from xml.dom import minidom
mname=["Group1", "Group2", "TimeGroup3", "RelayGroup1"]
mtype=["AccessControl", "AccessControl", "TimeAttendance", "RelayController"]
t=0;
body2="<login_request><username>defaultusername</username><password>defaultadmin</password></login_request>"
headers = {"Content-type": "application/xml"}
print (headers)
conn = http.client.HTTPConnection("hostname", 9090)
print (conn)
conn.request("POST", "/access/login", body2, headers)
response = conn.getresponse()
#print( response.status )
#print( response.read())
dat = minidom.parse(response)
tagname= dat.getElementsByTagName('sessionid')
sessionid=tagname[0].firstChild.data
headers2 = {'Content-type': 'application/xml', 'sessionid': sessionid}
print( headers2 )
for i in mname:
    print (i)
    body="<access_request><name>"+mname[t]+"</name><accesscollectiontype>"+mtype[t]+"</accesscollectiontype><keypadid>0</keypadid><timetableid>0</timetableid></access_request>"
    body=body.encode('utf-8')
    conn.request("POST", "/access/access/creategroup", body, headers2)
    response = conn.getresponse()
    print( response.status )
    print( response.read())
    print (body)
    t=t+1;
print (t)
conn.close()
