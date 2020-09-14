package dlfn3;
import java.io.*;
import java.net.*;
import java.time.LocalDate;
import java.util.*;
import org.json.*;
class dlfn3{public static void main(String[]a){
Scanner q=new Scanner(System.in);
String ot,ot3,oo="",oo3="",ov,
vo="",nn="",dt,cy,c2,qq="https://api.covid19api.com/summary",
qy="https://restcountries.eu/rest/v2",ne,q1="",q3,z=" ";float kk,rk,k;long tp=0;int i,ii,cd=1,cp=0,td,tdt,gc,tc,ct=0,pp,dc=1,e=1,ts=3,c01,c14,i4,i0=15;
HttpURLConnection cc,ccc,cc3;
try{cc=(HttpURLConnection)new URL(qq).openConnection();cc.connect();if(cc.getResponseCode()==200)
{BufferedReader in=new BufferedReader(new InputStreamReader(cc.getInputStream()));
while((ot=in.readLine())!=null){oo=oo+"\n"+ot;}
JSONObject o3=new JSONObject(oo);
ccc=(HttpURLConnection)new URL(qy).openConnection();
ccc.connect();
if(ccc.getResponseCode()==200)
{BufferedReader in1=new BufferedReader(new InputStreamReader(ccc.getInputStream()));
while((ov=in1.readLine())!=null){vo=vo+"\n"+ov;}
while(!q1.equals("0"))
{System.out.println("\nCode?(0>Exit)");q1=q.next();i=ii=0;tp=0;

if(q1.equals("EE")||
q1.equals("BG")||q1.equals("AT")
||q1.equals("LV")||q1.equals("FI")
)i0=200;
//else i0=20;

dt=(String)o3.get("Date");
                    td=(int)o3.getJSONObject("Global").get("TotalDeaths");
                    gc=(int)o3.getJSONObject("Global").get("TotalConfirmed");

Object[][]oj=new Object[186][3];
                    HashMap<String,Integer>hm=new HashMap<String,Integer>();

while(i<186)
                    {tdt=(int)o3.getJSONArray("Countries").getJSONObject(i).get("TotalDeaths");
                        cy=(String)o3.getJSONArray("Countries").getJSONObject(i).get("CountryCode");
                        tc=(int)o3.getJSONArray("Countries").getJSONObject(i).get("TotalConfirmed");oj[i][0]=cy;oj[i][1]=tdt;
hm.put(cy,tdt);
if(cy.equals(q1))
{ct=tc;if(tdt!=0){dc=cd=tdt;e=1;}
                        else{cd=1;dc=e=0;}
//System.out.println(cy+" covid dead: "+tdt+"\n"+cy+" covid case: "+tc);
                            
}i++;}

JSONArray pn=new JSONArray(vo);
Object[][]oi=new Object[250][3];
                    HashMap<String,Integer>h1=new HashMap<String,Integer>();
                    HashMap<String,Integer>h2=new HashMap<String,Integer>();

while(ii<250)
                    {pp=(int)pn.getJSONObject(ii).get("population");
                        c2=(String)pn.getJSONObject(ii).get("alpha2Code");
                        ne=(String)pn.getJSONObject(ii).get("name");
                        oi[ii][2]=ne;
                        oi[ii][0]=c2;oi[ii][1]=pp;
                        h1.put(c2,pp);h2.put(ne,pp);
                        if(c2.equals(q1)){cp=pp;nn=(String)pn.getJSONObject(ii).get("name");
//System.out.println(c2+" population: "+pp+"\n"+nn+" ...timeout "+ts+" sec...\n");
}tp=tp+pp;ii++;}

//Thread.sleep(ts*1000);
Object[][]mmm=new Object[186][3];
i=ii=0;int mm=0;while(i<186)
{String mm0=(String)oj[i][0];
int mm1=(int)oj[i][1];ii=0;
while(ii<250)
{String mn0=(String)oi[ii][0];
int mn1=(int)oi[ii][1];
if(mm0.equals(mn0))
{if(mm1!=0)mm=mn1/mm1;
else mm=mn1*10;
String mn2=(String)oi[ii][2];
                            System.out.println(mm0+" "+mm1+" <"+mn1+"> "+mm+" "+mn2);
ii=250;mmm[i][2]=mn2;
mmm[i][1]=mm;mmm[i][0]=mm0;}
ii++;}i++;};

boolean sr=false;
while(!sr){sr=true;
for(int j=0;j<185;j++){
if((int)mmm[j][1]>(int)mmm[j+1][1]){int tm=(int)mmm[j][1];
String tms=(String)mmm[j][0];
String tmn=(String)mmm[j][2];
mmm[j][1]=mmm[j+1][1];
mmm[j][0]=mmm[j+1][0];
mmm[j][2]=mmm[j+1][2];
mmm[j+1][1]=tm;mmm[j+1][0]=tms;
mmm[j+1][2]=tmn;sr=false;}}}
System.out.println();
/*System.out.println("\noi -population array:\n"+Arrays.deepToString(oi)+
"\noj -covid array:\n"+
Arrays.deepToString(oj)+"\nmmm -sort array:\n"+Arrays.deepToString(mmm)
+"\n"+"hm -hashmap:\n"+hm+"\nh1 -map1:\n"+h1+"\nh2 -map2:\n"+h2+"\n");*/

i=185;while(i>-1){
System.out.println(mmm[i][0]+
": died 1 in "+
Integer.toString((int)mmm[i][1])+" "+mmm[i][2]);i--;}
System.out.println("\nData from:\n"+qq+"\n"+qy+"\n\n"+dt+"\nWorld dead: "+td+"\ntotal case: "+gc+"\npopulation: "+tp+"\ndeath/pop.: 1 in "+tp/td+"\ncases/pop.: 1 in "+tp/gc+"\ndied/cases: 1 in "+gc/td+"\n\n"+nn+"\n"+dc+" in "+cp+" covid "+ct+"\ndead: "+e+" in "+cp/cd+"\ncase: 1 in "+cp/ct+"\ndied: "+e+" in "+ct/cd);

LocalDate t01=LocalDate.now().minusDays(1);
LocalDate t14=LocalDate.now().minusDays(16);
LocalDate t02=LocalDate.now().minusDays(2);
LocalDate t15=LocalDate.now().minusDays(15);
 q3="https://api.covid19api.com/country/"+nn+"/status/confirmed?from="+t14+"&to="+t01;

cc3=(HttpURLConnection)new URL(q3).openConnection();
cc3.connect();
if(cc3.getResponseCode()==200){
                        BufferedReader in3=new BufferedReader(new InputStreamReader(cc3.getInputStream()));
                        while((ot3=in3.readLine())!=null){oo3=oo3+"\n"+ot3;}
//System.out.println(oo3+"\n"+q3);
JSONArray o33=new JSONArray(oo3);
            c01=(int)o33.getJSONObject(0).get("Cases"); c14=(int)o33.getJSONObject(14).get("Cases");
rk=c14-c01;kk=rk*100000/cp;
                        System.out.println(

t02+" <==> "+t15
+"\n<"+c14+"-"+c01+"> "+(c14-c01)+" in "+cp
+"\n"+
"Last 2 weeks in 100 000: "+kk
);}oo3="";}}}
i4=i0;
LocalDate t01=LocalDate.now().minusDays(1);
LocalDate t14=LocalDate.now().minusDays(16+i0);
q3="https://api.covid19api.com/country/"+nn+"/status/confirmed?from="+t14+"&to="+t01;
cc3=(HttpURLConnection)new URL(q3).openConnection();cc3.connect();
if(cc3.getResponseCode()==200){BufferedReader in3=new BufferedReader(new InputStreamReader(cc3.getInputStream()));
            while((ot3=in3.readLine())!=null){oo3=oo3+"\n"+ot3;}}
//System.out.println("\n"+q3);
JSONArray o33=new JSONArray(oo3);
while(i0>0){
c01=(int)o33.getJSONObject(0+i0).get("Cases");
c14=(int)o33.getJSONObject(14+i0).get("Cases");
rk=c14-c01;kk=rk*100000/cp;
LocalDate t0=LocalDate.now().minusDays(i4-i0);q3=t0+" K.quarantine: ";

//System.out.println(q3+kk);

for(k=kk/2;k>0;k--)z=z+">";
if(kk>25)z=" >=>=>=>=>=>=>";
System.out.println(t0+z+" "+kk);z=" ";

i0--;}
//;System.out.println(0);
}catch(Throwable cs){cs.printStackTrace();}q.close();
//System.out.println("\nVariables Names\nCovid: qq -Site; oo -Data; o3 -Json\nCodes: qy -Site; vo -Data; pn -Json\nTotal: dt -Date; td -Dead; tp -Pop.\nLocal: nn -Name; cd -Dead; cp -Pop.\n");
}}

// Copy this code in your java IDE and run
// from here

package dlfn3;
import java.io.*;
import java.net.*;
import java.time.LocalDate;
import java.util.*;
import org.json.*;
class dlfn3{public static void main(String[]a){
Scanner q=new Scanner(System.in);
String ot,ot3,oo="",oo3="",ov,
vo="",nn="",dt,cy,c2,qq="https://api.covid19api.com/summary",
qy="https://restcountries.eu/rest/v2",ne,q1="",q3,z=" ";float kk,rk,k;long tp=0;int i,ii,cd=1,cp=0,td,tdt,gc,tc,ct=0,pp,dc=1,e=1,ts=3,c01,c14,i4,i0=15;
HttpURLConnection cc,ccc,cc3;
try{cc=(HttpURLConnection)new URL(qq).openConnection();cc.connect();if(cc.getResponseCode()==200)
{BufferedReader in=new BufferedReader(new InputStreamReader(cc.getInputStream()));
while((ot=in.readLine())!=null){oo=oo+"\n"+ot;}
JSONObject o3=new JSONObject(oo);
ccc=(HttpURLConnection)new URL(qy).openConnection();
ccc.connect();
if(ccc.getResponseCode()==200)
{BufferedReader in1=new BufferedReader(new InputStreamReader(ccc.getInputStream()));
while((ov=in1.readLine())!=null){vo=vo+"\n"+ov;}
while(!q1.equals("0"))
{System.out.println("\nCode?(0>Exit)");q1=q.next();i=ii=0;tp=0;

if(q1.equals("EE")||
q1.equals("BG")||q1.equals("AT")
||q1.equals("LV")||q1.equals("FI")
)i0=200;
//else i0=20;

dt=(String)o3.get("Date");
                    td=(int)o3.getJSONObject("Global").get("TotalDeaths");
                    gc=(int)o3.getJSONObject("Global").get("TotalConfirmed");

Object[][]oj=new Object[186][3];
                    HashMap<String,Integer>hm=new HashMap<String,Integer>();

while(i<186)
                    {tdt=(int)o3.getJSONArray("Countries").getJSONObject(i).get("TotalDeaths");
                        cy=(String)o3.getJSONArray("Countries").getJSONObject(i).get("CountryCode");
                        tc=(int)o3.getJSONArray("Countries").getJSONObject(i).get("TotalConfirmed");oj[i][0]=cy;oj[i][1]=tdt;
hm.put(cy,tdt);
if(cy.equals(q1))
{ct=tc;if(tdt!=0){dc=cd=tdt;e=1;}
                        else{cd=1;dc=e=0;}
//System.out.println(cy+" covid dead: "+tdt+"\n"+cy+" covid case: "+tc);
                            
}i++;}

JSONArray pn=new JSONArray(vo);
Object[][]oi=new Object[250][3];
                    HashMap<String,Integer>h1=new HashMap<String,Integer>();
                    HashMap<String,Integer>h2=new HashMap<String,Integer>();

while(ii<250)
                    {pp=(int)pn.getJSONObject(ii).get("population");
                        c2=(String)pn.getJSONObject(ii).get("alpha2Code");
                        ne=(String)pn.getJSONObject(ii).get("name");
                        oi[ii][2]=ne;
                        oi[ii][0]=c2;oi[ii][1]=pp;
                        h1.put(c2,pp);h2.put(ne,pp);
                        if(c2.equals(q1)){cp=pp;nn=(String)pn.getJSONObject(ii).get("name");
//System.out.println(c2+" population: "+pp+"\n"+nn+" ...timeout "+ts+" sec...\n");
}tp=tp+pp;ii++;}

//Thread.sleep(ts*1000);
Object[][]mmm=new Object[186][3];
i=ii=0;int mm=0;while(i<186)
{String mm0=(String)oj[i][0];
int mm1=(int)oj[i][1];ii=0;
while(ii<250)
{String mn0=(String)oi[ii][0];
int mn1=(int)oi[ii][1];
if(mm0.equals(mn0))
{if(mm1!=0)mm=mn1/mm1;
else mm=mn1*10;
String mn2=(String)oi[ii][2];
                            System.out.println(mm0+" "+mm1+" <"+mn1+"> "+mm+" "+mn2);
ii=250;mmm[i][2]=mn2;
mmm[i][1]=mm;mmm[i][0]=mm0;}
ii++;}i++;};

boolean sr=false;
while(!sr){sr=true;
for(int j=0;j<185;j++){
if((int)mmm[j][1]>(int)mmm[j+1][1]){int tm=(int)mmm[j][1];
String tms=(String)mmm[j][0];
String tmn=(String)mmm[j][2];
mmm[j][1]=mmm[j+1][1];
mmm[j][0]=mmm[j+1][0];
mmm[j][2]=mmm[j+1][2];
mmm[j+1][1]=tm;mmm[j+1][0]=tms;
mmm[j+1][2]=tmn;sr=false;}}}
System.out.println();
/*System.out.println("\noi -population array:\n"+Arrays.deepToString(oi)+
"\noj -covid array:\n"+
Arrays.deepToString(oj)+"\nmmm -sort array:\n"+Arrays.deepToString(mmm)
+"\n"+"hm -hashmap:\n"+hm+"\nh1 -map1:\n"+h1+"\nh2 -map2:\n"+h2+"\n");*/

i=185;while(i>-1){
System.out.println(mmm[i][0]+
": died 1 in "+
Integer.toString((int)mmm[i][1])+" "+mmm[i][2]);i--;}
System.out.println("\nData from:\n"+qq+"\n"+qy+"\n\n"+dt+"\nWorld dead: "+td+"\ntotal case: "+gc+"\npopulation: "+tp+"\ndeath/pop.: 1 in "+tp/td+"\ncases/pop.: 1 in "+tp/gc+"\ndied/cases: 1 in "+gc/td+"\n\n"+nn+"\n"+dc+" in "+cp+" covid "+ct+"\ndead: "+e+" in "+cp/cd+"\ncase: 1 in "+cp/ct+"\ndied: "+e+" in "+ct/cd);

LocalDate t01=LocalDate.now().minusDays(1);
LocalDate t14=LocalDate.now().minusDays(16);
LocalDate t02=LocalDate.now().minusDays(2);
LocalDate t15=LocalDate.now().minusDays(15);
 q3="https://api.covid19api.com/country/"+nn+"/status/confirmed?from="+t14+"&to="+t01;

cc3=(HttpURLConnection)new URL(q3).openConnection();
cc3.connect();
if(cc3.getResponseCode()==200){
                        BufferedReader in3=new BufferedReader(new InputStreamReader(cc3.getInputStream()));
                        while((ot3=in3.readLine())!=null){oo3=oo3+"\n"+ot3;}
//System.out.println(oo3+"\n"+q3);
JSONArray o33=new JSONArray(oo3);
            c01=(int)o33.getJSONObject(0).get("Cases"); c14=(int)o33.getJSONObject(14).get("Cases");
rk=c14-c01;kk=rk*100000/cp;
                        System.out.println(

t02+" <==> "+t15
+"\n<"+c14+"-"+c01+"> "+(c14-c01)+" in "+cp
+"\n"+
"Last 2 weeks in 100 000: "+kk
);}oo3="";}}}
i4=i0;
LocalDate t01=LocalDate.now().minusDays(1);
LocalDate t14=LocalDate.now().minusDays(16+i0);
q3="https://api.covid19api.com/country/"+nn+"/status/confirmed?from="+t14+"&to="+t01;
cc3=(HttpURLConnection)new URL(q3).openConnection();cc3.connect();
if(cc3.getResponseCode()==200){BufferedReader in3=new BufferedReader(new InputStreamReader(cc3.getInputStream()));
            while((ot3=in3.readLine())!=null){oo3=oo3+"\n"+ot3;}}
//System.out.println("\n"+q3);
JSONArray o33=new JSONArray(oo3);
while(i0>0){
c01=(int)o33.getJSONObject(0+i0).get("Cases");
c14=(int)o33.getJSONObject(14+i0).get("Cases");
rk=c14-c01;kk=rk*100000/cp;
LocalDate t0=LocalDate.now().minusDays(i4-i0);q3=t0+" K.quarantine: ";

//System.out.println(q3+kk);

for(k=kk/2;k>0;k--)z=z+">";
if(kk>25)z=" >=>=>=>=>=>=>";
System.out.println(t0+z+" "+kk);z=" ";

i0--;}
//;System.out.println(0);
}catch(Throwable cs){cs.printStackTrace();}q.close();
//System.out.println("\nVariables Names\nCovid: qq -Site; oo -Data; o3 -Json\nCodes: qy -Site; vo -Data; pn -Json\nTotal: dt -Date; td -Dead; tp -Pop.\nLocal: nn -Name; cd -Dead; cp -Pop.\n");
}}

// to here

# covid19
# covid19
