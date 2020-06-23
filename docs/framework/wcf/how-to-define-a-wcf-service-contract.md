---
title: 教學課程：定義 Windows Communication Foundation 服務合約
description: 瞭解如何將服務合約定義為一系列文章的一部分，以協助您開始建立 WCF 應用程式。
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 5cb371da8c7180b8c4cbf5ac11468fbb8e0e13cc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246307"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="e2db3-103">教學課程：定義 Windows Communication Foundation 服務合約</span><span class="sxs-lookup"><span data-stu-id="e2db3-103">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="e2db3-104">本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第一個。</span><span class="sxs-lookup"><span data-stu-id="e2db3-104">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="e2db3-105">如需教學課程的總覽，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="e2db3-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="e2db3-106">當您建立 WCF 服務時，您的第一項工作是定義服務合約。</span><span class="sxs-lookup"><span data-stu-id="e2db3-106">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="e2db3-107">服務合約會指定服務所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="e2db3-107">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="e2db3-108">作業可以視為一種 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="e2db3-108">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="e2db3-109">您可以藉由定義 c # 或 Visual Basic 介面來建立服務合約。</span><span class="sxs-lookup"><span data-stu-id="e2db3-109">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="e2db3-110">介面具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="e2db3-110">An interface has the following characteristics:</span></span>

- <span data-ttu-id="e2db3-111">介面中的每個方法會對應一個特定服務作業。</span><span class="sxs-lookup"><span data-stu-id="e2db3-111">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="e2db3-112">針對每個介面，您必須套用 <xref:System.ServiceModel.ServiceContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e2db3-112">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="e2db3-113">針對每個作業/方法，您必須套用 <xref:System.ServiceModel.OperationContractAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="e2db3-113">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="e2db3-114">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="e2db3-114">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e2db3-115">建立**WCF 服務程式庫**專案。</span><span class="sxs-lookup"><span data-stu-id="e2db3-115">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="e2db3-116">定義服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="e2db3-116">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="e2db3-117">建立 WCF 服務程式庫專案和定義服務合約介面</span><span class="sxs-lookup"><span data-stu-id="e2db3-117">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="e2db3-118">以系統管理員身分開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e2db3-118">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="e2db3-119">若要這麼做，請在 [**開始**] 功能表中選取 [Visual Studio] 程式，然後從快捷方式功能表選取 [**更多**  >  **以系統管理員身分執行**]。</span><span class="sxs-lookup"><span data-stu-id="e2db3-119">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="e2db3-120">建立**WCF 服務程式庫**專案。</span><span class="sxs-lookup"><span data-stu-id="e2db3-120">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="e2db3-121">從 [檔案]\*\*\*\* 功能表選取 [新增]\*\*\*\* > [專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e2db3-121">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="e2db3-122">在 [**新增專案**] 對話方塊左側，展開 [ **Visual c #** ] 或 [ **Visual Basic**]，然後選取 [ **WCF** ] 分類。</span><span class="sxs-lookup"><span data-stu-id="e2db3-122">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="e2db3-123">Visual Studio 會在視窗的中間區段顯示專案範本清單。</span><span class="sxs-lookup"><span data-stu-id="e2db3-123">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="e2db3-124">選取 [ **WCF 服務程式庫**]。</span><span class="sxs-lookup"><span data-stu-id="e2db3-124">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="e2db3-125">如果您沒有看到 [ **WCF**專案範本] 類別目錄，您可能需要安裝 Visual Studio 的**Windows Communication Foundation**元件。</span><span class="sxs-lookup"><span data-stu-id="e2db3-125">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="e2db3-126">在 [**新增專案**] 對話方塊中，選取左側的 [**開啟 Visual Studio 安裝程式**] 連結。</span><span class="sxs-lookup"><span data-stu-id="e2db3-126">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="e2db3-127">選取 [**個別元件**] 索引標籤，然後尋找並選取 [**開發活動**] 類別底下的 [ **Windows Communication Foundation** ]。</span><span class="sxs-lookup"><span data-stu-id="e2db3-127">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="e2db3-128">選擇 [**修改**] 開始安裝元件。</span><span class="sxs-lookup"><span data-stu-id="e2db3-128">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="e2db3-129">在視窗的下方區段中，針對 [**名稱**] 輸入*GettingStartedLib* ，然後在 [**方案名稱**] 中輸入*GettingStarted* 。</span><span class="sxs-lookup"><span data-stu-id="e2db3-129">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="e2db3-130">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e2db3-130">Select **OK**.</span></span>

      <span data-ttu-id="e2db3-131">Visual Studio 會建立專案，其中包含三個檔案： *IService1.cs* （或 Visual Basic 專案的*IService1* ）、 *Service1.cs* （或 Visual Basic 專案的*Service1* ）和*App.config*。Visual Studio 定義這些檔案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e2db3-131">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="e2db3-132">*IService1*檔案包含服務合約的預設定義。</span><span class="sxs-lookup"><span data-stu-id="e2db3-132">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="e2db3-133">*Service1*檔案包含服務合約的預設執行。</span><span class="sxs-lookup"><span data-stu-id="e2db3-133">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="e2db3-134">*App.config*檔案包含使用 Visual Studio WCF 服務主機工具載入預設服務所需的設定資訊。</span><span class="sxs-lookup"><span data-stu-id="e2db3-134">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="e2db3-135">如需 WCF 服務主機工具的詳細資訊，請參閱[Wcf 服務主機（WcfSvcHost.exe）](wcf-service-host-wcfsvchost-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="e2db3-135">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="e2db3-136">如果您已使用 Visual Basic 的開發人員環境設定來安裝 Visual Studio，解決方案可能會隱藏起來。</span><span class="sxs-lookup"><span data-stu-id="e2db3-136">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="e2db3-137">如果是這種情況，請從 [**工具**] 功能表中選取 [**選項**]，然後選取 [選項] 視窗中的 [**專案和方案**]  >  **[一般**]。 **Options**</span><span class="sxs-lookup"><span data-stu-id="e2db3-137">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="e2db3-138">選取 [**永遠顯示方案**]。</span><span class="sxs-lookup"><span data-stu-id="e2db3-138">Select **Always show solution**.</span></span> <span data-ttu-id="e2db3-139">此外，請確認已選取 [**建立時儲存新專案**]。</span><span class="sxs-lookup"><span data-stu-id="e2db3-139">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="e2db3-140">從**方案總管**開啟**IService1.cs**或**IService1**檔案，並將其程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e2db3-140">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="e2db3-141">本合約定義了線上計算機。</span><span class="sxs-lookup"><span data-stu-id="e2db3-141">This contract defines an online calculator.</span></span> <span data-ttu-id="e2db3-142">請注意， `ICalculator` 介面是以 <xref:System.ServiceModel.ServiceContractAttribute> 屬性標記（簡化為 `ServiceContract` ）。</span><span class="sxs-lookup"><span data-stu-id="e2db3-142">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="e2db3-143">這個屬性會定義命名空間來區分合約名稱。</span><span class="sxs-lookup"><span data-stu-id="e2db3-143">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="e2db3-144">程式碼會使用屬性來標示每個計算機作業 <xref:System.ServiceModel.OperationContractAttribute> （簡化為 `OperationContract` ）。</span><span class="sxs-lookup"><span data-stu-id="e2db3-144">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e2db3-145">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e2db3-145">Next steps</span></span>

<span data-ttu-id="e2db3-146">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="e2db3-146">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="e2db3-147">建立 WCF 服務程式庫專案。</span><span class="sxs-lookup"><span data-stu-id="e2db3-147">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="e2db3-148">定義服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="e2db3-148">Define a service contract interface.</span></span>

<span data-ttu-id="e2db3-149">請前進到下一個教學課程，以瞭解如何執行 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="e2db3-149">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e2db3-150">教學課程：執行 WCF 服務合約</span><span class="sxs-lookup"><span data-stu-id="e2db3-150">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
