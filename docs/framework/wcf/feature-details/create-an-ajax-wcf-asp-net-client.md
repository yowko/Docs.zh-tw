---
title: HOW TO：建立啟用 AJAX 的 WCF 服務和存取該服務的 ASP.NET 用戶端
ms.date: 03/30/2017
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
ms.openlocfilehash: 58971d11ab76112627dd81d53381236932268e25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490626"
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a>HOW TO：建立啟用 AJAX 的 WCF 服務和存取該服務的 ASP.NET 用戶端
本主題示範如何使用 Visual Studio 2008 建立啟用 AJAX 的 Windows Communication Foundation (WCF) 服務和存取該服務的 ASP.NET 用戶端。 「程序」一節將說明服務與用戶端的程式碼建立步驟，並接著在「範例」一節提供服務與用戶端的程式碼範例。  
  
### <a name="to-create-the-aspnet-client-application"></a>若要建立 ASP.NET 用戶端應用程式  
  
1.  開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
2.  從**檔案**功能表上，選取**新增**，然後**專案**，然後**Web**，然後選取**ASP.NET Web 應用程式**.  
  
3.  將專案命名`SandwichServices`按一下**確定**。  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a>若要建立啟用 AJAX 的 WCF 服務  
  
1.  以滑鼠右鍵按一下`SandwichServices`專案中**方案總管 中**視窗，然後選取**新增**，然後**新項目**，然後**啟用 AJAX 的 WCF 服務**.  
  
2.  為服務名稱`CostService`中**名稱**方塊，然後按一下**新增**。  
  
3.  開啟 CostService.svc.cs 檔案。  
  
4.  指定`Namespace`如<xref:System.ServiceModel.ServiceContractAttribute>為`SandwichService`:  
  
    ```  
    namespace SandwichServices  
    {  
      [ServiceContract(Namespace = "SandwichServices")]  
      [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
       public class CostService  
       {  
         …  
       }  
     }  
    ```  
  
5.  在服務中實作作業。 將 <xref:System.ServiceModel.OperationContractAttribute> 加入至每項作業中，以表示這些作業是合約的一部分。 下列範例會實作可傳回特定三明治數量成本的方法。  
  
    ```  
    public class CostService  
    {  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
    // Add more operations here and mark them with [OperationContract]  
    }  
    ```  
  
### <a name="to-configure-the-client-to-access-the-service"></a>若要設定用戶端存取服務  
  
1.  開啟 Default.aspx 頁面上，然後選取**設計**檢視。  
  
2.  從**檢視**功能表上，選取**工具箱**。  
  
3.  展開**AJAX 擴充功能**節點拖曳和卸除**ScriptManager** Default.aspx 頁面上。  
  
4.  以滑鼠右鍵按一下**ScriptManager**選取**屬性**。  
  
5.  展開**服務**集合**屬性**開啟的視窗**ServiceReference 集合編輯器**視窗。  
  
6.  按一下**新增**，指定`CostService.svc`為**路徑**參考，然後按一下**確定**。  
  
7.  展開**HTML**節點**工具箱**拖曳和卸除**輸入 （按鈕）** Default.aspx 頁面上。  
  
8.  以滑鼠右鍵按一下**按鈕**選取**屬性**。  
  
9. 變更**值**欄位設為`Price for 3 Sandwiches`。  
  
10. 按兩下**按鈕**存取 JavaScript 程式碼。  
  
11. 下列 JavaScript 程式碼中傳遞 <`script`> 項目。  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a>若要從用戶端存取服務  
  
1.  使用 Ctrl +F5 來啟動服務與 Web 用戶端。 按一下**個 3 烤三明治的價錢**按鈕以產生預期的"3.75"輸出。  
  
## <a name="example"></a>範例  
 此範例包含 WCFService.svc.cs 檔案中內含的服務程式碼，以及 Default.aspx 檔案中內含的用戶端程式碼。  
  
```  
//The service code contained in the CostService.svc.cs file.  
  
using System;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Activation;  
using System.ServiceModel.Web;  
  
namespace SandwichServices  
{  
    [ServiceContract(Namespace="SandwichServices")]  
    [AspNetCompatibilityRequirements(RequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
    public class CostService  
    {  
        // Add [WebGet] attribute to use HTTP GET  
        [OperationContract]  
        public double CostOfSandwiches(int quantity)  
        {  
            return 1.25 * quantity;  
        }  
  
        // Add more operations here and mark them with [OperationContract]  
    }  
}  
//The code for hosting the service is contained in the CostService.svc file.  
  
<%@ ServiceHost Language="C#" Debug="true" Service="SandwichServices.CostService" CodeBehind="CostService.svc.cs" %>  
  
//The client code contained in the Default.aspx file.  
  
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Default.aspx.cs" Inherits="SandwichServices._Default" %>  
  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
  
<html >  
<head runat="server">  
    <title>Untitled Page</title>  
<script language="javascript" type="text/javascript">  
// <!CDATA[  
  
function Button1_onclick() {  
var service = new SandwichServices.CostService();  
service.CostOfSandwiches(3, onSuccess, null, null);  
}  
  
function onSuccess(result){  
alert(result);  
}  
  
// ]]>  
</script>  
</head>  
<body>  
    <form id="form1" runat="server">  
    <div>  
  
    </div>  
    <asp:ScriptManager ID="ScriptManager1" runat="server">  
        <services>  
            <asp:servicereference Path="CostService.svc" />  
        </services>  
    </asp:ScriptManager>  
    </form>  
    <p>  
        <input id="Button1" type="button" value="Price for 3 Sandwiches" onclick="return Button1_onclick()" /></p>  
</body>  
</html>  
```     
