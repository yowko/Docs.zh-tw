---
title: "HOW TO：定義 Windows Communication Foundation 服務合約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: service contracts [WCF], defining
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
caps.latest.revision: "58"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c69f79d8629acee80a2e59346032e7733ec37dea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="cfdca-102">HOW TO：定義 Windows Communication Foundation 服務合約</span><span class="sxs-lookup"><span data-stu-id="cfdca-102">How to: Define a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="cfdca-103">這是在建立基本 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式時必須進行的六項工作中的第一項。</span><span class="sxs-lookup"><span data-stu-id="cfdca-103">This is the first of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="cfdca-104">六個工作的概觀，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。</span><span class="sxs-lookup"><span data-stu-id="cfdca-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="cfdca-105">建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務時，第一項工作是要定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="cfdca-105">When creating a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service, the first task is to define a service contract.</span></span> <span data-ttu-id="cfdca-106">服務合約會指定服務所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="cfdca-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="cfdca-107">作業可以視為一種 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="cfdca-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="cfdca-108">合約可以透過定義 C++、C# 或 Visual Basic (VB) 介面來建立。</span><span class="sxs-lookup"><span data-stu-id="cfdca-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="cfdca-109">介面中的每一個方法都會對應到一個特定的服務作業。</span><span class="sxs-lookup"><span data-stu-id="cfdca-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="cfdca-110">每一個介面都要有套用一個 <xref:System.ServiceModel.ServiceContractAttribute>，而且每一個作業都必須套用一個 <xref:System.ServiceModel.OperationContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cfdca-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="cfdca-111">如果具有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性之介面中的方法沒有 <xref:System.ServiceModel.OperationContractAttribute> 屬性，服務就不會公開該方法。</span><span class="sxs-lookup"><span data-stu-id="cfdca-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>  
  
 <span data-ttu-id="cfdca-112">用於這項工作的程式碼將於本程序之後的範例中提供。</span><span class="sxs-lookup"><span data-stu-id="cfdca-112">The code used for this task is provided in the example following the procedure.</span></span>  
  
### <a name="to-define-a-service-contract"></a><span data-ttu-id="cfdca-113">若要定義服務合約</span><span class="sxs-lookup"><span data-stu-id="cfdca-113">To define a service contract</span></span>  
  
1.  <span data-ttu-id="cfdca-114">開啟[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]身為系統管理員，以滑鼠右鍵按一下中的程式**啟動**功能表，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="cfdca-114">Open  [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] as an administrator by right-clicking the program in the **Start** menu and selecting **Run as administrator**.</span></span>  
  
2.  <span data-ttu-id="cfdca-115">建立 WCF 服務程式庫專案，依序按一下**檔案**功能表，然後選取**新增**，**專案**。</span><span class="sxs-lookup"><span data-stu-id="cfdca-115">Create a WCF Service Library project by clicking the **File** menu and selecting **New**, **Project**.</span></span> <span data-ttu-id="cfdca-116">在**新專案** 對話方塊中，在對話方塊的左側展開**Visual C#** C# 專案或**其他語言**然後**Visual Basic** Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="cfdca-116">In the **New Project** dialog, on the left-hand side of the dialog expand **Visual C#** for a C# project or **Other Languages** and then **Visual Basic** for a Visual Basic project.</span></span> <span data-ttu-id="cfdca-117">在 選取的語言下選取**WCF**和專案範本清單將會顯示在對話方塊中間區段。</span><span class="sxs-lookup"><span data-stu-id="cfdca-117">Under the language selected select **WCF** and a list of project templates will be displayed on the center section of the dialog.</span></span> <span data-ttu-id="cfdca-118">選取**WCF 服務程式庫**，並輸入`GettingStartedLib`中**名稱**文字方塊和`GettingStarted`中**方案名稱**在對話方塊底部的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="cfdca-118">Select **WCF Service Library**, and type `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>  
  
3.  <span data-ttu-id="cfdca-119">Visual Studio 將會建立包含下列 3 個檔案的專案：IService1.cs (或 IService1.vb)、Service1.cs (或 Service1.vb) 和 App.config。IService1 檔案包含預設服務合約。</span><span class="sxs-lookup"><span data-stu-id="cfdca-119">Visual Studio will create the project which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config.  The IService1 file contains a default service contract.</span></span>  <span data-ttu-id="cfdca-120">Service1 檔案包含服務合約的預設實作。</span><span class="sxs-lookup"><span data-stu-id="cfdca-120">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="cfdca-121">App.config 檔案包含載入預設服務與 Visual Studio WCF 服務主機所需的組態。</span><span class="sxs-lookup"><span data-stu-id="cfdca-121">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="cfdca-122">如需 WCF 服務主機工具的詳細資訊，請參閱[WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="cfdca-122">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>  
  
4.  <span data-ttu-id="cfdca-123">開啟 IService1.cs 或 IService1.vb 檔案，刪除命名空間宣告內的程式碼，僅保留命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="cfdca-123">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration leaving the namespace declaration.</span></span> <span data-ttu-id="cfdca-124">在命名空間宣告中，定義名為 `ICalculator` 的新介面，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cfdca-124">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>  
  
    ```  
    // IService.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
    namespace GettingStartedLib  
    {  
            [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
            public interface ICalculator  
            {  
                [OperationContract]  
                double Add(double n1, double n2);  
                [OperationContract]  
                double Subtract(double n1, double n2);  
                [OperationContract]  
                double Multiply(double n1, double n2);  
                [OperationContract]  
                double Divide(double n1, double n2);  
            }  
    }  
    ```  
  
    ```  
    ‘IService.vb  
    Imports System  
    Imports System.ServiceModel  
  
    Namespace GettingStartedLib  
  
        <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _  
        Public Interface ICalculator  
  
            <OperationContract()> _  
            Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double  
            <OperationContract()> _  
            Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double  
        End Interface  
    End Namespace  
    ```  
  
     <span data-ttu-id="cfdca-125">本合約定義了線上計算機。</span><span class="sxs-lookup"><span data-stu-id="cfdca-125">This contract defines an online calculator.</span></span> <span data-ttu-id="cfdca-126">注意 `ICalculator` 介面有標示 <xref:System.ServiceModel.ServiceContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cfdca-126">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="cfdca-127">這個屬性會定義用來釐清合約名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="cfdca-127">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="cfdca-128">每個計算機作業都會標示 <xref:System.ServiceModel.OperationContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cfdca-128">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cfdca-129">使用屬性來標註介面、成員或類別時，您可以在屬性名稱中省略 "Attribute" 的部分。</span><span class="sxs-lookup"><span data-stu-id="cfdca-129">When using attributes to annotate an interface, member, or class, you can drop the "Attribute" part from the attribute name.</span></span> <span data-ttu-id="cfdca-130">因此，<xref:System.ServiceModel.ServiceContractAttribute> 在 C# 中會變成 `[ServiceContract]`，而在 Visual Basic 中會變成 `<ServiceContract>`。</span><span class="sxs-lookup"><span data-stu-id="cfdca-130">So <xref:System.ServiceModel.ServiceContractAttribute> becomes `[ServiceContract]` in C#, or `<ServiceContract>` in Visual Basic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdca-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="cfdca-131">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [<span data-ttu-id="cfdca-132">如何：履行服務合約</span><span class="sxs-lookup"><span data-stu-id="cfdca-132">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 [<span data-ttu-id="cfdca-133">快速入門</span><span class="sxs-lookup"><span data-stu-id="cfdca-133">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="cfdca-134">自我裝載</span><span class="sxs-lookup"><span data-stu-id="cfdca-134">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
