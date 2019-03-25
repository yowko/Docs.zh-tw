---
title: 教學課程：定義 Windows Communication Foundation 服務合約
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: f93ef787c74a4581d45c24c5a704cc5fb044bd46
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409961"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="13ce2-102">教學課程：定義 Windows Communication Foundation 服務合約</span><span class="sxs-lookup"><span data-stu-id="13ce2-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="13ce2-103">本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作中的第一個。</span><span class="sxs-lookup"><span data-stu-id="13ce2-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="13ce2-104">如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="13ce2-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="13ce2-105">當您建立 WCF 服務時，您的第一個工作是定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="13ce2-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="13ce2-106">服務合約會指定服務所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="13ce2-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="13ce2-107">作業可以視為一種 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="13ce2-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="13ce2-108">您建立服務合約定義視覺效果C#或 Visual Basic (VB) 介面。</span><span class="sxs-lookup"><span data-stu-id="13ce2-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="13ce2-109">介面具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="13ce2-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="13ce2-110">介面中的每一個方法都會對應到一個特定的服務作業。</span><span class="sxs-lookup"><span data-stu-id="13ce2-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="13ce2-111">對於每個介面，您必須套用<xref:System.ServiceModel.ServiceContractAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="13ce2-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="13ce2-112">對於每個作業/方法，您必須套用<xref:System.ServiceModel.OperationContractAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="13ce2-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="13ce2-113">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="13ce2-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="13ce2-114">建立**WCF 服務程式庫**專案。</span><span class="sxs-lookup"><span data-stu-id="13ce2-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="13ce2-115">定義服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="13ce2-115">Define a service contract interface.</span></span>


## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="13ce2-116">建立 WCF 服務程式庫專案，並定義服務合約介面</span><span class="sxs-lookup"><span data-stu-id="13ce2-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="13ce2-117">系統管理員身分開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="13ce2-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="13ce2-118">若要這樣做，請選取 [Visual Studio 方案中的**開始**] 功能表，然後選取**詳細** > **系統管理員身分執行**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="13ce2-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="13ce2-119">建立**WCF 服務程式庫**專案。</span><span class="sxs-lookup"><span data-stu-id="13ce2-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="13ce2-120">從 [檔案] 功能表選取 [新增] > [專案]。</span><span class="sxs-lookup"><span data-stu-id="13ce2-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="13ce2-121">在**新的專案** 對話方塊的左側，展開**Visual C#** 或**Visual Basic**，然後選取**WCF**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="13ce2-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="13ce2-122">Visual Studio 視窗的中間區段中顯示專案範本的清單。</span><span class="sxs-lookup"><span data-stu-id="13ce2-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="13ce2-123">選取  **WCF 服務程式庫**。</span><span class="sxs-lookup"><span data-stu-id="13ce2-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="13ce2-124">如果您沒有看到**WCF**專案範本類別，您可能需要安裝**Windows Communication Foundation** Visual Studio 的元件。</span><span class="sxs-lookup"><span data-stu-id="13ce2-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="13ce2-125">在 **新的專案**對話方塊中，選取**開啟 Visual Studio 安裝程式**左側的連結。</span><span class="sxs-lookup"><span data-stu-id="13ce2-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="13ce2-126">選取 **個別元件**索引標籤，然後尋找並選取**Windows Communication Foundation**之下**開發活動**類別目錄。</span><span class="sxs-lookup"><span data-stu-id="13ce2-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="13ce2-127">選擇**修改**開始安裝元件。</span><span class="sxs-lookup"><span data-stu-id="13ce2-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="13ce2-128">在視窗的底部區段中，輸入*GettingStartedLib* for**名稱**並*GettingStarted*如**方案名稱**。</span><span class="sxs-lookup"><span data-stu-id="13ce2-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="13ce2-129">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="13ce2-129">Select **OK**.</span></span>

      <span data-ttu-id="13ce2-130">Visual Studio 會建立專案，其中有三個檔案：*將 IService1.cs* (或*IService1.vb* Visual Basic 專案)， *Service1.cs* (或*Service1.vb* Visual Basic 專案)，和*App.config*。Visual Studio 會定義這些檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="13ce2-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="13ce2-131">*IService1*檔案包含服務合約的預設定義。</span><span class="sxs-lookup"><span data-stu-id="13ce2-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="13ce2-132">*Service1*檔案包含服務合約的預設實作。</span><span class="sxs-lookup"><span data-stu-id="13ce2-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="13ce2-133">*App.config*檔案包含載入預設服務與 Visual Studio WCF 服務主機工具所需的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="13ce2-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="13ce2-134">如需 WCF 服務主機工具的詳細資訊，請參閱[WCF 服務主機 (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="13ce2-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="13ce2-135">如果您安裝 Visual Studio 與 Visual Basic 開發人員環境設定時，可能會隱藏方案。</span><span class="sxs-lookup"><span data-stu-id="13ce2-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="13ce2-136">如果發生這種情況，請選取**選項**從**工具**功能表，然後選取**專案和方案** > **一般**中**選項**視窗。</span><span class="sxs-lookup"><span data-stu-id="13ce2-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="13ce2-137">選取 **一律顯示方案**。</span><span class="sxs-lookup"><span data-stu-id="13ce2-137">Select **Always show solution**.</span></span> <span data-ttu-id="13ce2-138">此外，確認**儲存新專案時建立**已選取。</span><span class="sxs-lookup"><span data-stu-id="13ce2-138">Also, verify that **Save new projects when created** is selected.</span></span>


3. <span data-ttu-id="13ce2-139">從**方案總管**，開啟**IService1.cs**或是**IService1.vb**檔案，並以下列程式碼取代其程式碼：</span><span class="sxs-lookup"><span data-stu-id="13ce2-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="13ce2-140">本合約定義了線上計算機。</span><span class="sxs-lookup"><span data-stu-id="13ce2-140">This contract defines an online calculator.</span></span> <span data-ttu-id="13ce2-141">請注意`ICalculator`介面會標示<xref:System.ServiceModel.ServiceContractAttribute>屬性 (為簡化`ServiceContract`)。</span><span class="sxs-lookup"><span data-stu-id="13ce2-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="13ce2-142">此屬性定義命名空間，以釐清合約名稱。</span><span class="sxs-lookup"><span data-stu-id="13ce2-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="13ce2-143">程式碼將標記與每個計算機作業<xref:System.ServiceModel.OperationContractAttribute>屬性 (為簡化`OperationContract`)。</span><span class="sxs-lookup"><span data-stu-id="13ce2-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="13ce2-144">後續步驟</span><span class="sxs-lookup"><span data-stu-id="13ce2-144">Next steps</span></span>

<span data-ttu-id="13ce2-145">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="13ce2-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="13ce2-146">建立 WCF 服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="13ce2-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="13ce2-147">定義服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="13ce2-147">Define a service contract interface.</span></span>

<span data-ttu-id="13ce2-148">請前進到下一個教學課程，以了解如何實作 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="13ce2-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="13ce2-149">教學課程：實作 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="13ce2-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
