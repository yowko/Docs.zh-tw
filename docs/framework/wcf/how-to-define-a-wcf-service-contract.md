---
title: 教學課程：定義 Windows Communication Foundation 服務合約
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: ba88fc6ba4cba8d46ed1b43080d471b1b7c4bd75
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928879"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="8910b-102">教學課程：定義 Windows Communication Foundation 服務合約</span><span class="sxs-lookup"><span data-stu-id="8910b-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="8910b-103">本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第一個。</span><span class="sxs-lookup"><span data-stu-id="8910b-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="8910b-104">如需教學課程的總覽，請[參閱教學課程：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。</span><span class="sxs-lookup"><span data-stu-id="8910b-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="8910b-105">當您建立 WCF 服務時，您的第一項工作是定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="8910b-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="8910b-106">服務合約會指定服務所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="8910b-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="8910b-107">作業可以視為一種 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="8910b-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="8910b-108">您可以藉由定義視覺效果C#或 VISUAL BASIC （VB）介面來建立服務合約。</span><span class="sxs-lookup"><span data-stu-id="8910b-108">You create service contracts by defining a Visual C# or Visual Basic (VB) interface.</span></span> <span data-ttu-id="8910b-109">介面具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="8910b-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="8910b-110">介面中的每一個方法都會對應到一個特定的服務作業。</span><span class="sxs-lookup"><span data-stu-id="8910b-110">Each method in the interface corresponds to a specific service operation.</span></span> 
- <span data-ttu-id="8910b-111">針對每個介面，您必須<xref:System.ServiceModel.ServiceContractAttribute>套用屬性。</span><span class="sxs-lookup"><span data-stu-id="8910b-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="8910b-112">針對每個作業/方法，您必須<xref:System.ServiceModel.OperationContractAttribute>套用屬性。</span><span class="sxs-lookup"><span data-stu-id="8910b-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> 

<span data-ttu-id="8910b-113">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="8910b-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8910b-114">建立**WCF 服務程式庫**專案。</span><span class="sxs-lookup"><span data-stu-id="8910b-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="8910b-115">定義服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="8910b-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="8910b-116">建立 WCF 服務程式庫專案和定義服務合約介面</span><span class="sxs-lookup"><span data-stu-id="8910b-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="8910b-117">以系統管理員身分開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="8910b-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="8910b-118">若要這麼做，請在 [**開始**] 功能表中選取 [Visual Studio] 程式，然後從快捷方式功能表選取 [**更多** > **以系統管理員身分執行**]。</span><span class="sxs-lookup"><span data-stu-id="8910b-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="8910b-119">建立**WCF 服務程式庫**專案。</span><span class="sxs-lookup"><span data-stu-id="8910b-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="8910b-120">從 [檔案] 功能表選取 [新增] > [專案]。</span><span class="sxs-lookup"><span data-stu-id="8910b-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="8910b-121">在 [**新增專案**] 對話方塊左側，展開 [**視覺效果C#**  ] 或 [ **Visual Basic**]，然後選取 [ **WCF** ] 分類。</span><span class="sxs-lookup"><span data-stu-id="8910b-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="8910b-122">Visual Studio 會在視窗的中間區段顯示專案範本清單。</span><span class="sxs-lookup"><span data-stu-id="8910b-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="8910b-123">選取 [ **WCF 服務程式庫**]。</span><span class="sxs-lookup"><span data-stu-id="8910b-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="8910b-124">如果您沒有看到 [ **WCF**專案範本] 類別目錄，您可能需要安裝 Visual Studio 的**Windows Communication Foundation**元件。</span><span class="sxs-lookup"><span data-stu-id="8910b-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="8910b-125">在 [**新增專案**] 對話方塊中，選取左側的 [**開啟 Visual Studio 安裝程式**] 連結。</span><span class="sxs-lookup"><span data-stu-id="8910b-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="8910b-126">選取 [**個別元件**] 索引標籤，然後尋找並選取 [**開發活動**] 類別底下的 [ **Windows Communication Foundation** ]。</span><span class="sxs-lookup"><span data-stu-id="8910b-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="8910b-127">選擇 [**修改**] 開始安裝元件。</span><span class="sxs-lookup"><span data-stu-id="8910b-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="8910b-128">在視窗的下方區段中，針對 [**名稱**] 輸入*GettingStartedLib* ，然後在 [**方案名稱**] 中輸入*GettingStarted* 。</span><span class="sxs-lookup"><span data-stu-id="8910b-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span> 

   4. <span data-ttu-id="8910b-129">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="8910b-129">Select **OK**.</span></span>

      <span data-ttu-id="8910b-130">Visual Studio 會建立專案，其中包含三個檔案：*IService1.cs* （或適用于 Visual Basic 專案的*IService1* ）、 *Service1.cs* （或 Visual Basic 專案的*Service1* ）和*app.config*。Visual Studio 定義這些檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="8910b-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span> 
      - <span data-ttu-id="8910b-131">*IService1*檔案包含服務合約的預設定義。</span><span class="sxs-lookup"><span data-stu-id="8910b-131">The *IService1* file contains the default definition of the service contract.</span></span> 
      - <span data-ttu-id="8910b-132">*Service1*檔案包含服務合約的預設執行。</span><span class="sxs-lookup"><span data-stu-id="8910b-132">The *Service1* file contains the default implementation of the service contract.</span></span> 
      - <span data-ttu-id="8910b-133">*App.config*檔案包含使用 Visual Studio WCF 服務主機工具載入預設服務時所需的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="8910b-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="8910b-134">如需 WCF 服務主機工具的詳細資訊，請參閱[Wcf 服務主機（WcfSvcHost .exe）](wcf-service-host-wcfsvchost-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="8910b-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="8910b-135">如果您已使用 Visual Basic 的開發人員環境設定來安裝 Visual Studio，解決方案可能會隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="8910b-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="8910b-136">如果是這種情況，請從 [**工具**] 功能表中選取 [**選項**]，然後選取 [**選項**] 視窗中的 [**專案和方案** > ] **[一般**]。</span><span class="sxs-lookup"><span data-stu-id="8910b-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="8910b-137">選取 [**永遠顯示方案**]。</span><span class="sxs-lookup"><span data-stu-id="8910b-137">Select **Always show solution**.</span></span> <span data-ttu-id="8910b-138">此外，請確認已選取 [**建立時儲存新專案**]。</span><span class="sxs-lookup"><span data-stu-id="8910b-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="8910b-139">從**方案總管**開啟**IService1.cs**或**IService1**檔案，並將其程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="8910b-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="8910b-140">本合約定義了線上計算機。</span><span class="sxs-lookup"><span data-stu-id="8910b-140">This contract defines an online calculator.</span></span> <span data-ttu-id="8910b-141">請注意`ICalculator` ，介面是<xref:System.ServiceModel.ServiceContractAttribute>以屬性標記（簡化為`ServiceContract`）。</span><span class="sxs-lookup"><span data-stu-id="8910b-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="8910b-142">這個屬性會定義命名空間來區分合約名稱。</span><span class="sxs-lookup"><span data-stu-id="8910b-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="8910b-143">程式碼會使用<xref:System.ServiceModel.OperationContractAttribute>屬性來標示每個計算機作業（簡化為`OperationContract`）。</span><span class="sxs-lookup"><span data-stu-id="8910b-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8910b-144">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8910b-144">Next steps</span></span>

<span data-ttu-id="8910b-145">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="8910b-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8910b-146">建立 WCF 服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="8910b-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="8910b-147">定義服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="8910b-147">Define a service contract interface.</span></span>

<span data-ttu-id="8910b-148">請前進到下一個教學課程，以瞭解如何執行 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="8910b-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8910b-149">教學課程：執行 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="8910b-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
