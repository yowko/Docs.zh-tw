---
title: HOW TO：定義 Windows Communication Foundation 服務合約
ms.date: 09/14/2018
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 4f85a51c47eb045d1d2f0111cb217199c9acf0d7
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537874"
---
# <a name="how-to-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="82e6a-102">HOW TO：定義 Windows Communication Foundation 服務合約</span><span class="sxs-lookup"><span data-stu-id="82e6a-102">How to: Define a Windows Communication Foundation Service Contract</span></span>

<span data-ttu-id="82e6a-103">這是建立基本的 Windows Communication Foundation (WCF) 應用程式所需的六項工作中的第一個。</span><span class="sxs-lookup"><span data-stu-id="82e6a-103">This is the first of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="82e6a-104">如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。</span><span class="sxs-lookup"><span data-stu-id="82e6a-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

 <span data-ttu-id="82e6a-105">建立 WCF 服務時，第一項工作是定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="82e6a-105">When creating a WCF service, the first task is to define a service contract.</span></span> <span data-ttu-id="82e6a-106">服務合約會指定服務所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="82e6a-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="82e6a-107">作業可以視為一種 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="82e6a-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="82e6a-108">合約可以透過定義 C++、C# 或 Visual Basic (VB) 介面來建立。</span><span class="sxs-lookup"><span data-stu-id="82e6a-108">Contracts are created by defining a C++, C#, or Visual Basic (VB) interface.</span></span> <span data-ttu-id="82e6a-109">介面中的每一個方法都會對應到一個特定的服務作業。</span><span class="sxs-lookup"><span data-stu-id="82e6a-109">Each method in the interface corresponds to a specific service operation.</span></span> <span data-ttu-id="82e6a-110">每一個介面都要有套用一個 <xref:System.ServiceModel.ServiceContractAttribute>，而且每一個作業都必須套用一個 <xref:System.ServiceModel.OperationContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="82e6a-110">Each interface must have the <xref:System.ServiceModel.ServiceContractAttribute> applied to it and each operation must have the <xref:System.ServiceModel.OperationContractAttribute> attribute applied to it.</span></span> <span data-ttu-id="82e6a-111">如果具有 <xref:System.ServiceModel.ServiceContractAttribute> 屬性之介面中的方法沒有 <xref:System.ServiceModel.OperationContractAttribute> 屬性，服務就不會公開該方法。</span><span class="sxs-lookup"><span data-stu-id="82e6a-111">If a method within an interface that has the <xref:System.ServiceModel.ServiceContractAttribute> attribute does not have the <xref:System.ServiceModel.OperationContractAttribute> attribute, that method is not exposed by the service.</span></span>

 <span data-ttu-id="82e6a-112">用於這項工作的程式碼將於本程序之後的範例中提供。</span><span class="sxs-lookup"><span data-stu-id="82e6a-112">The code used for this task is provided in the example following the procedure.</span></span>

## <a name="define-a-service-contract"></a><span data-ttu-id="82e6a-113">定義服務合約</span><span class="sxs-lookup"><span data-stu-id="82e6a-113">Define a service contract</span></span>

1. <span data-ttu-id="82e6a-114">系統管理員身分開啟 Visual Studio 中的程式上按一下滑鼠右鍵**開始**功能表，然後選取**詳細** > **系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="82e6a-114">Open Visual Studio as an administrator by right-clicking the program in the **Start** menu and selecting **More** > **Run as administrator**.</span></span>

2. <span data-ttu-id="82e6a-115">建立 WCF 服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="82e6a-115">Create a WCF Service Library project.</span></span>

   1. <span data-ttu-id="82e6a-116">從 [檔案] 功能表選取 [新增] > [專案]。</span><span class="sxs-lookup"><span data-stu-id="82e6a-116">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="82e6a-117">在**新的專案** 對話方塊的左側，展開**Visual C#** 或**Visual Basic**，然後選取**WCF**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="82e6a-117">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="82e6a-118">專案範本清單會顯示在對話方塊中間區段。</span><span class="sxs-lookup"><span data-stu-id="82e6a-118">A list of project templates is displayed in the center section of the dialog.</span></span> <span data-ttu-id="82e6a-119">選取  **WCF 服務程式庫**。</span><span class="sxs-lookup"><span data-stu-id="82e6a-119">Select **WCF Service Library**.</span></span>

   3. <span data-ttu-id="82e6a-120">輸入`GettingStartedLib`中**名稱**文字方塊中並`GettingStarted`中**方案名稱**在對話方塊底部的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="82e6a-120">Enter `GettingStartedLib` in the **Name** textbox and `GettingStarted` in the **Solution name** textbox at the bottom of the dialog.</span></span>

   > [!NOTE]
   > <span data-ttu-id="82e6a-121">如果您沒有看到**WCF**專案範本類別，您可能需要安裝**Windows Communication Foundation** Visual Studio 的元件。</span><span class="sxs-lookup"><span data-stu-id="82e6a-121">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="82e6a-122">在 **新的專案**對話方塊方塊中，按一下連結**開啟 Visual Studio 安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="82e6a-122">In the **New Project** dialog box, click the link that says **Open Visual Studio Installer**.</span></span> <span data-ttu-id="82e6a-123">選取 **個別元件**索引標籤，然後尋找並選取**Windows Communication Foundation**之下**開發活動**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="82e6a-123">Select the **Individual Components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="82e6a-124">選擇**修改**開始安裝元件。</span><span class="sxs-lookup"><span data-stu-id="82e6a-124">Choose **Modify** to begin installing the component.</span></span>

   <span data-ttu-id="82e6a-125">Visual Studio 會建立含有 3 個檔案的專案： IService1.cs （或 IService1.vb） service1.vb （或 Service1.vb） 和 App.config。IService1 檔案包含預設服務合約。</span><span class="sxs-lookup"><span data-stu-id="82e6a-125">Visual Studio creates the project, which contains 3 files: IService1.cs (or IService1.vb), Service1.cs (or Service1.vb), and App.config. The IService1 file contains a default service contract.</span></span> <span data-ttu-id="82e6a-126">Service1 檔案包含服務合約的預設實作。</span><span class="sxs-lookup"><span data-stu-id="82e6a-126">The Service1 file contains a default implementation of the service contract.</span></span> <span data-ttu-id="82e6a-127">App.config 檔案包含載入預設服務與 Visual Studio WCF 服務主機所需的組態。</span><span class="sxs-lookup"><span data-stu-id="82e6a-127">The App.config file contains configuration needed to load the default service with the Visual Studio WCF Service Host.</span></span> <span data-ttu-id="82e6a-128">如需 WCF 服務主機工具的詳細資訊，請參閱[WCF 服務主機 (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="82e6a-128">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)</span></span>

3. <span data-ttu-id="82e6a-129">開啟 IService1.cs 或 IService1.vb 檔案，並刪除命名空間宣告，讓命名空間宣告內的程式碼。</span><span class="sxs-lookup"><span data-stu-id="82e6a-129">Open the IService1.cs or IService1.vb file and delete the code within the namespace declaration, leaving the namespace declaration.</span></span> <span data-ttu-id="82e6a-130">在命名空間宣告中，定義名為 `ICalculator` 的新介面，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="82e6a-130">Inside the namespace declaration define a new interface called `ICalculator` as shown in the code below.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;

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

    ```vb
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

     <span data-ttu-id="82e6a-131">本合約定義了線上計算機。</span><span class="sxs-lookup"><span data-stu-id="82e6a-131">This contract defines an online calculator.</span></span> <span data-ttu-id="82e6a-132">注意 `ICalculator` 介面有標示 <xref:System.ServiceModel.ServiceContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="82e6a-132">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="82e6a-133">這個屬性會定義用來釐清合約名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="82e6a-133">This attribute defines a namespace that is used to disambiguate the contract name.</span></span> <span data-ttu-id="82e6a-134">每個計算機作業都會標示 <xref:System.ServiceModel.OperationContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="82e6a-134">Each calculator operation is marked with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

## <a name="next-steps"></a><span data-ttu-id="82e6a-135">後續步驟</span><span class="sxs-lookup"><span data-stu-id="82e6a-135">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="82e6a-136">如何： 實作服務合約</span><span class="sxs-lookup"><span data-stu-id="82e6a-136">How to: Implement a service contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

## <a name="see-also"></a><span data-ttu-id="82e6a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82e6a-137">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- [<span data-ttu-id="82e6a-138">如何：履行服務合約</span><span class="sxs-lookup"><span data-stu-id="82e6a-138">How to: Implement a Service Contract</span></span>](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)
- [<span data-ttu-id="82e6a-139">快速入門</span><span class="sxs-lookup"><span data-stu-id="82e6a-139">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="82e6a-140">自我裝載</span><span class="sxs-lookup"><span data-stu-id="82e6a-140">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)