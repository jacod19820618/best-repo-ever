# best-repo-ever

public with sharing class Pdfimage{   
public List<Payment__C> Paylist {get; set;}
      public String imageUrl{get;set;} //CH07
  
       public Pdfimage(){
        Paylist = [SELECT Id, Name  FROM Payment__C
                        WHERE Id =: Apexpages.currentPage().getParameters().get('Id')];
                       
      imageUrl='https://www.barcodesinc.com/generator/image.php?code='+Paylist.get(0).name+'&style=325&type=C128B&width=200&height=50&xres=1&font=3';
     
      }
        
}
 In visualforce page add like below :
<apex:page showHeader="false" sidebar="false" controller="Pdfimage" cache="false" standardstylesheets="false" renderAs="pdf" applyHtmlTag="false">
    <html>
         <table>
                <tr>
                  <td colspan="8">         
                    <apex:image value="{!imageUrl}"/>
                  </td>
                </tr>
          </table>
      </html>
</apex:page>
