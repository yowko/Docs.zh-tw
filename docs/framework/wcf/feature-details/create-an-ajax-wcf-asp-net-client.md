---
title: "HOW TO：建立啟用 AJAX 的 WCF 服務和存取該服務的 ASP.NET 用戶端"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95012df8-2a66-420d-944a-8afab261013e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aafa15129e4a131c5f50eb3296a87fc141e1bda6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-an-ajax-enabled-wcf-service-and-an-aspnet-client-that-accesses-the-service"></a><span data-ttu-id="b60da-102">HOW TO：建立啟用 AJAX 的 WCF 服務和存取該服務的 ASP.NET 用戶端</span><span class="sxs-lookup"><span data-stu-id="b60da-102">How to: Create an AJAX-Enabled WCF Service and an ASP.NET Client that Accesses the Service</span></span>
<span data-ttu-id="b60da-103">本主題說明如何使用 Visual Studio 2008 來建立啟用 AJAX 的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務，以及可存取該服務的 ASP.NET 用戶端。</span><span class="sxs-lookup"><span data-stu-id="b60da-103">This topic shows how to use Visual Studio 2008 to create an AJAX-enabled [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and an ASP.NET client that accesses the service.</span></span> <span data-ttu-id="b60da-104">「程序」一節將說明服務與用戶端的程式碼建立步驟，並接著在「範例」一節提供服務與用戶端的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="b60da-104">The code for the service and for the client are provided in the Example section after the steps for creating them are described in the Procedures section.</span></span>  
  
### <a name="to-create-the-aspnet-client-application"></a><span data-ttu-id="b60da-105">若要建立 ASP.NET 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="b60da-105">To create the ASP.NET client application</span></span>  
  
1.  <span data-ttu-id="b60da-106">開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b60da-106">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="b60da-107">從**檔案**功能表上，選取**新增**，然後**專案**，然後**Web**，然後選取**ASP.NET Web 應用程式**.</span><span class="sxs-lookup"><span data-stu-id="b60da-107">From the **File** menu, select **New**, then **Project**, then **Web**, and then select **ASP.NET Web Application**.</span></span>  
  
3.  <span data-ttu-id="b60da-108">將專案命名`SandwichServices`按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b60da-108">Name the Project `SandwichServices` and click **OK**.</span></span>  
  
### <a name="to-create-the-wcf-ajax-enabled-service"></a><span data-ttu-id="b60da-109">若要建立啟用 AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="b60da-109">To create the WCF AJAX-enabled service</span></span>  
  
1.  <span data-ttu-id="b60da-110">以滑鼠右鍵按一下`SandwichServices`專案中**方案總管 中**視窗，然後選取**新增**，然後**新項目**，然後**啟用 AJAX 的 WCF 服務**.</span><span class="sxs-lookup"><span data-stu-id="b60da-110">Right-click the `SandwichServices` project in the **Solution Explorer** window and select **Add**, then **New Item**, and then **AJAX-enabled WCF Service**.</span></span>  
  
2.  <span data-ttu-id="b60da-111">為服務名稱`CostService`中**名稱**方塊，然後按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="b60da-111">Name the service `CostService` in the **Name** box and click **Add**.</span></span>  
  
3.  <span data-ttu-id="b60da-112">開啟 CostService.svc.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="b60da-112">Open the CostService.svc.cs file.</span></span>  
  
4.  <span data-ttu-id="b60da-113">指定`Namespace`如<xref:System.ServiceModel.ServiceContractAttribute>為`SandwichService`:</span><span class="sxs-lookup"><span data-stu-id="b60da-113">Specify the `Namespace` for <xref:System.ServiceModel.ServiceContractAttribute> as `SandwichService`:</span></span>  
  
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
  
5.  <span data-ttu-id="b60da-114">在服務中實作作業。</span><span class="sxs-lookup"><span data-stu-id="b60da-114">Implement the operations in the service.</span></span> <span data-ttu-id="b60da-115">將 <xref:System.ServiceModel.OperationContractAttribute> 加入至每項作業中，以表示這些作業是合約的一部分。</span><span class="sxs-lookup"><span data-stu-id="b60da-115">Add the <xref:System.ServiceModel.OperationContractAttribute> to each of the operations to indicate that they are part of the contract.</span></span> <span data-ttu-id="b60da-116">下列範例會實作可傳回特定三明治數量成本的方法。</span><span class="sxs-lookup"><span data-stu-id="b60da-116">The following example implements a method that returns the cost of a given quantity of sandwiches.</span></span>  
  
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
  
### <a name="to-configure-the-client-to-access-the-service"></a><span data-ttu-id="b60da-117">若要設定用戶端存取服務</span><span class="sxs-lookup"><span data-stu-id="b60da-117">To configure the client to access the service</span></span>  
  
1.  <span data-ttu-id="b60da-118">開啟 Default.aspx 頁面上，然後選取**設計**檢視。</span><span class="sxs-lookup"><span data-stu-id="b60da-118">Open the Default.aspx page and select the **Design** view.</span></span>  
  
2.  <span data-ttu-id="b60da-119">從**檢視**功能表上，選取**工具箱**。</span><span class="sxs-lookup"><span data-stu-id="b60da-119">From the **View** menu, select **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="b60da-120">展開**AJAX 擴充功能**節點拖曳和卸除**ScriptManager** Default.aspx 頁面上。</span><span class="sxs-lookup"><span data-stu-id="b60da-120">Expand the **AJAX Extensions** node and drag and drop a **ScriptManager** on to the Default.aspx page.</span></span>  
  
4.  <span data-ttu-id="b60da-121">以滑鼠右鍵按一下**ScriptManager**選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b60da-121">Right-click the **ScriptManager** and select **Properties**.</span></span>  
  
5.  <span data-ttu-id="b60da-122">展開**服務**集合**屬性**開啟的視窗**ServiceReference 集合編輯器**視窗。</span><span class="sxs-lookup"><span data-stu-id="b60da-122">Expand the **Services** collection in the **Properties** window to open up the **ServiceReference Collection Editor** window.</span></span>  
  
6.  <span data-ttu-id="b60da-123">按一下**新增**，指定`CostService.svc`為**路徑**參考，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b60da-123">Click **Add**, specify `CostService.svc` as the **Path** referenced, and click **OK**.</span></span>  
  
7.  <span data-ttu-id="b60da-124">展開**HTML**節點**工具箱**拖曳和卸除**輸入 （按鈕）** Default.aspx 頁面上。</span><span class="sxs-lookup"><span data-stu-id="b60da-124">Expand the **HTML** node in the **Toolbox** and drag and drop an **Input (Button)** on to the Default.aspx page.</span></span>  
  
8.  <span data-ttu-id="b60da-125">以滑鼠右鍵按一下**按鈕**選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="b60da-125">Right-click the **Button** and select **Properties**.</span></span>  
  
9. <span data-ttu-id="b60da-126">變更**值**欄位設為`Price for 3 Sandwiches`。</span><span class="sxs-lookup"><span data-stu-id="b60da-126">Change the **Value** field to `Price for 3 Sandwiches`.</span></span>  
  
10. <span data-ttu-id="b60da-127">按兩下**按鈕**存取 JavaScript 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b60da-127">Double-click the **Button** to access the JavaScript code.</span></span>  
  
11. <span data-ttu-id="b60da-128">下列 JavaScript 程式碼中傳遞 <`script`> 項目。</span><span class="sxs-lookup"><span data-stu-id="b60da-128">Pass in the following JavaScript code within the <`script`> element.</span></span>  
  
    ```  
    function Button1_onclick() {  
    var service = new SandwichServices.CostService();  
    service.CostOfSandwiches(3, onSuccess, null, null);  
    }  
  
    function onSuccess(result){  
    alert(result);  
    }  
    ```  
  
### <a name="to-access-the-service-from-the-client"></a><span data-ttu-id="b60da-129">若要從用戶端存取服務</span><span class="sxs-lookup"><span data-stu-id="b60da-129">To access the service from the client</span></span>  
  
1.  <span data-ttu-id="b60da-130">使用 Ctrl +F5 來啟動服務與 Web 用戶端。</span><span class="sxs-lookup"><span data-stu-id="b60da-130">Use Ctrl +F5 to launch the service and the Web client.</span></span> <span data-ttu-id="b60da-131">按一下**個 3 烤三明治的價錢**按鈕以產生預期的"3.75"輸出。</span><span class="sxs-lookup"><span data-stu-id="b60da-131">Click the **Price for 3 Grilled Sandwiches** button to generate the expected output of "3.75".</span></span>  
  
## <a name="example"></a><span data-ttu-id="b60da-132">範例</span><span class="sxs-lookup"><span data-stu-id="b60da-132">Example</span></span>  
 <span data-ttu-id="b60da-133">此範例包含 WCFService.svc.cs 檔案中內含的服務程式碼，以及 Default.aspx 檔案中內含的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="b60da-133">This example contains the service code contained in the WCFService.svc.cs file and the client code contained in the Default.aspx file.</span></span>  
  
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
