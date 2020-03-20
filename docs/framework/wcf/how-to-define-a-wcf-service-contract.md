---
title: 教程：定義 Windows 通信基礎服務協定
ms.date: 03/19/2019
helpviewer_keywords:
- service contracts [WCF], defining
dev_langs:
- CSharp
- VB
ms.assetid: 67bf05b7-1d08-4911-83b7-a45d0b036fc3
ms.openlocfilehash: 7c1c42c4f22a1a9627c147440e8e198551470b7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184098"
---
# <a name="tutorial-define-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="013da-102">教程：定義 Windows 通信基礎服務協定</span><span class="sxs-lookup"><span data-stu-id="013da-102">Tutorial: Define a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="013da-103">本教程介紹創建基本 Windows 通信基礎 （WCF） 應用程式所需的五項任務中的第一個。</span><span class="sxs-lookup"><span data-stu-id="013da-103">This tutorial describes the first of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="013da-104">有關教程的概述，請參閱[教程：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="013da-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="013da-105">創建 WCF 服務時，您的第一個任務是定義服務協定。</span><span class="sxs-lookup"><span data-stu-id="013da-105">When you create a WCF service, your first task is to define a service contract.</span></span> <span data-ttu-id="013da-106">服務合約會指定服務所支援的作業。</span><span class="sxs-lookup"><span data-stu-id="013da-106">The service contract specifies what operations the service supports.</span></span> <span data-ttu-id="013da-107">作業可以視為一種 Web 服務方法。</span><span class="sxs-lookup"><span data-stu-id="013da-107">An operation can be thought of as a Web service method.</span></span> <span data-ttu-id="013da-108">通過定義 C# 或視覺化基本介面來創建服務協定。</span><span class="sxs-lookup"><span data-stu-id="013da-108">You create service contracts by defining a C# or Visual Basic interface.</span></span> <span data-ttu-id="013da-109">介面具有以下特徵：</span><span class="sxs-lookup"><span data-stu-id="013da-109">An interface has the following characteristics:</span></span>

- <span data-ttu-id="013da-110">介面中的每個方法會對應一個特定服務作業。</span><span class="sxs-lookup"><span data-stu-id="013da-110">Each method in the interface corresponds to a specific service operation.</span></span>
- <span data-ttu-id="013da-111">對於每個介面，必須應用該<xref:System.ServiceModel.ServiceContractAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="013da-111">For each interface, you must apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span>
- <span data-ttu-id="013da-112">對於每個操作/方法，必須應用該<xref:System.ServiceModel.OperationContractAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="013da-112">For each operation/method, you must apply the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span>

<span data-ttu-id="013da-113">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="013da-113">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="013da-114">創建**WCF 服務庫**專案。</span><span class="sxs-lookup"><span data-stu-id="013da-114">Create a **WCF Service Library** project.</span></span>
> - <span data-ttu-id="013da-115">定義服務協定介面。</span><span class="sxs-lookup"><span data-stu-id="013da-115">Define a service contract interface.</span></span>

## <a name="create-a-wcf-service-library-project-and-define-a-service-contract-interface"></a><span data-ttu-id="013da-116">創建 WCF 服務庫專案並定義服務協定介面</span><span class="sxs-lookup"><span data-stu-id="013da-116">Create a WCF Service Library project and define a service contract interface</span></span>

1. <span data-ttu-id="013da-117">以系統管理員身分開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="013da-117">Open Visual Studio as an administrator.</span></span> <span data-ttu-id="013da-118">為此，請在 **"開始"** 功能表中選擇 Visual Studio 程式，然後從快顯功能表中選擇 **"以管理員** > **身份運行**"。</span><span class="sxs-lookup"><span data-stu-id="013da-118">To do so, select the Visual Studio program in the **Start** menu, and then select **More** > **Run as administrator** from the shortcut menu.</span></span>

2. <span data-ttu-id="013da-119">創建**WCF 服務庫**專案。</span><span class="sxs-lookup"><span data-stu-id="013da-119">Create a **WCF Service Library** project.</span></span>

   1. <span data-ttu-id="013da-120">從 [檔案]\*\*\*\* 功能表選取 [新增]\*\*\*\* > [專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="013da-120">From the **File** menu, select **New** > **Project**.</span></span>

   2. <span data-ttu-id="013da-121">在左側的 **"新專案**"對話方塊中，展開**視覺化 C#** 或**視覺化基本**，然後選擇**WCF**類別。</span><span class="sxs-lookup"><span data-stu-id="013da-121">In the **New Project** dialog, on the left-hand side, expand **Visual C#** or **Visual Basic**, and then select the **WCF** category.</span></span> <span data-ttu-id="013da-122">Visual Studio 在視窗的中心部分顯示專案範本的清單。</span><span class="sxs-lookup"><span data-stu-id="013da-122">Visual Studio displays a list of project templates in the center section of the window.</span></span> <span data-ttu-id="013da-123">選擇**WCF 服務庫**。</span><span class="sxs-lookup"><span data-stu-id="013da-123">Select **WCF Service Library**.</span></span>

      > [!NOTE]
      > <span data-ttu-id="013da-124">如果您沒有看到**WCF**專案範本類別，則可能需要安裝 Visual Studio 的**Windows 通信基礎**元件。</span><span class="sxs-lookup"><span data-stu-id="013da-124">If you don't see the **WCF** project template category, you may need to install the **Windows Communication Foundation** component of Visual Studio.</span></span> <span data-ttu-id="013da-125">在 **"新專案**"對話方塊中，選擇左側的 **"打開視覺化工作室安裝程式"** 連結。</span><span class="sxs-lookup"><span data-stu-id="013da-125">In the **New Project** dialog box, select the **Open Visual Studio Installer** link on the left side.</span></span> <span data-ttu-id="013da-126">選擇 **"單個元件**"選項卡，然後在 **"開發活動**"類別下查找並選擇**Windows 通信基礎**。</span><span class="sxs-lookup"><span data-stu-id="013da-126">Select the **Individual components** tab, and then find and select **Windows Communication Foundation** under the **Development activities** category.</span></span> <span data-ttu-id="013da-127">選擇 **"修改"** 以開始安裝元件。</span><span class="sxs-lookup"><span data-stu-id="013da-127">Choose **Modify** to begin installing the component.</span></span>

   3. <span data-ttu-id="013da-128">在視窗的底部部分，輸入"獲取*入門Lib"\***以**獲取**解決方案名稱的名稱**和*入門\*。</span><span class="sxs-lookup"><span data-stu-id="013da-128">In the bottom section of the window, enter *GettingStartedLib* for the **Name** and *GettingStarted* for the **Solution name**.</span></span>

   4. <span data-ttu-id="013da-129">選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="013da-129">Select **OK**.</span></span>

      <span data-ttu-id="013da-130">Visual Studio 創建的專案有三個檔 *：IService1.cs（* 或用於視覺化基礎專案的*IService1.vb）、Service1.cs（* 或 Visual Basic 專案的*Service1.vb）* 和*App.config*。 *Service1.cs*Visual Studio 定義這些檔如下所示：</span><span class="sxs-lookup"><span data-stu-id="013da-130">Visual Studio creates the project, which has three files: *IService1.cs* (or *IService1.vb* for a Visual Basic project), *Service1.cs* (or *Service1.vb* for a Visual Basic project), and *App.config*. Visual Studio defines these files as follows:</span></span>
      - <span data-ttu-id="013da-131">*IService1*檔包含服務協定的預設定義。</span><span class="sxs-lookup"><span data-stu-id="013da-131">The *IService1* file contains the default definition of the service contract.</span></span>
      - <span data-ttu-id="013da-132">*Service1*檔包含服務協定的預設實現。</span><span class="sxs-lookup"><span data-stu-id="013da-132">The *Service1* file contains the default implementation of the service contract.</span></span>
      - <span data-ttu-id="013da-133">*App.config*檔包含使用 Visual Studio WCF 服務主機工具載入預設服務所需的配置資訊。</span><span class="sxs-lookup"><span data-stu-id="013da-133">The *App.config* file contains the configuration info needed to load the default service with the Visual Studio WCF Service Host tool.</span></span> <span data-ttu-id="013da-134">有關 WCF 服務主機工具的詳細資訊，請參閱[WCF 服務主機 （WcfSvcHost.exe）。](wcf-service-host-wcfsvchost-exe.md)</span><span class="sxs-lookup"><span data-stu-id="013da-134">For more information about the WCF Service Host tool, see [WCF Service Host (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md).</span></span>

      > [!NOTE]
      > <span data-ttu-id="013da-135">如果安裝了具有視覺化基本開發人員環境設置的 Visual Studio，則解決方案可能已隱藏。</span><span class="sxs-lookup"><span data-stu-id="013da-135">If you installed Visual Studio with Visual Basic developer environment settings, the solution might be hidden.</span></span> <span data-ttu-id="013da-136">如果是這種情況，請從 **"工具"** 功能表中選擇 **"選項**"，然後在 **"選項"** 視窗中選擇"**專案和解決方案** > **常規**"。</span><span class="sxs-lookup"><span data-stu-id="013da-136">If this is the case, select **Options** from the **Tools** menu, then select **Projects and Solutions** > **General** in the **Options** window.</span></span> <span data-ttu-id="013da-137">選擇 **"始終顯示解決方案**"。</span><span class="sxs-lookup"><span data-stu-id="013da-137">Select **Always show solution**.</span></span> <span data-ttu-id="013da-138">此外，驗證是否選擇了**創建時保存新專案**。</span><span class="sxs-lookup"><span data-stu-id="013da-138">Also, verify that **Save new projects when created** is selected.</span></span>

3. <span data-ttu-id="013da-139">從**解決方案資源管理器**中打開**IService1.cs**或**IService1.vb**檔，並將其代碼替換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="013da-139">From **Solution Explorer**, open the **IService1.cs** or **IService1.vb** file, and replace its code with the following code:</span></span>

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

     <span data-ttu-id="013da-140">本合約定義了線上計算機。</span><span class="sxs-lookup"><span data-stu-id="013da-140">This contract defines an online calculator.</span></span> <span data-ttu-id="013da-141">請注意，`ICalculator`介面用<xref:System.ServiceModel.ServiceContractAttribute>屬性標記（簡化為`ServiceContract`）。</span><span class="sxs-lookup"><span data-stu-id="013da-141">Notice the `ICalculator` interface is marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute (simplified as `ServiceContract`).</span></span> <span data-ttu-id="013da-142">此屬性定義命名空間以消除協定名稱的歧義。</span><span class="sxs-lookup"><span data-stu-id="013da-142">This attribute defines a namespace to disambiguate the contract name.</span></span> <span data-ttu-id="013da-143">代碼使用<xref:System.ServiceModel.OperationContractAttribute>屬性標記每個計算機操作（簡化為`OperationContract`）。</span><span class="sxs-lookup"><span data-stu-id="013da-143">The code marks each calculator operation with the <xref:System.ServiceModel.OperationContractAttribute> attribute (simplified as `OperationContract`).</span></span>

## <a name="next-steps"></a><span data-ttu-id="013da-144">後續步驟</span><span class="sxs-lookup"><span data-stu-id="013da-144">Next steps</span></span>

<span data-ttu-id="013da-145">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="013da-145">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="013da-146">創建 WCF 服務庫專案。</span><span class="sxs-lookup"><span data-stu-id="013da-146">Create a WCF Service Library project.</span></span>
> - <span data-ttu-id="013da-147">定義服務協定介面。</span><span class="sxs-lookup"><span data-stu-id="013da-147">Define a service contract interface.</span></span>

<span data-ttu-id="013da-148">進入下一個教程，瞭解如何實現 WCF 服務協定。</span><span class="sxs-lookup"><span data-stu-id="013da-148">Advance to the next tutorial to learn how to implement the WCF service contract.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="013da-149">教程：實現 WCF 服務協定</span><span class="sxs-lookup"><span data-stu-id="013da-149">Tutorial: Implement a WCF service contract</span></span>](how-to-implement-a-wcf-contract.md)
