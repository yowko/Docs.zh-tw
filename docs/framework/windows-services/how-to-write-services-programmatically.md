---
title: 作法：以程式設計方式撰寫服務
description: 瞭解如何自行設定繼承和其他基礎結構元素，以程式設計方式撰寫服務。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
ms.openlocfilehash: cd749d325bec6636243dec1905f79abb5e42f04e
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608396"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="e44a8-103">作法：以程式設計方式撰寫服務</span><span class="sxs-lookup"><span data-stu-id="e44a8-103">How to: Write Services Programmatically</span></span>
<span data-ttu-id="e44a8-104">如果您選擇不使用 Windows 服務專案範本，則可以藉由自行設定繼承和其他基礎結構元素來撰寫自己的服務。</span><span class="sxs-lookup"><span data-stu-id="e44a8-104">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="e44a8-105">當您以程式設計方式建立服務時，必須執行範本會為您處理的數個步驟：</span><span class="sxs-lookup"><span data-stu-id="e44a8-105">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
- <span data-ttu-id="e44a8-106">您必須將服務類別設定為繼承自 <xref:System.ServiceProcess.ServiceBase> 類別。</span><span class="sxs-lookup"><span data-stu-id="e44a8-106">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
- <span data-ttu-id="e44a8-107">您必須建立服務專案的 `Main` 方法，以定義要執行的服務並在其上呼叫 <xref:System.ServiceProcess.ServiceBase.Run%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="e44a8-107">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
- <span data-ttu-id="e44a8-108">您必須覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 程序，並填入任何要執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e44a8-108">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="e44a8-109">以程式設計方式撰寫服務</span><span class="sxs-lookup"><span data-stu-id="e44a8-109">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="e44a8-110">依照下列步驟來建立空白的專案，並建立必要命名空間的參考：</span><span class="sxs-lookup"><span data-stu-id="e44a8-110">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1. <span data-ttu-id="e44a8-111">在 [方案總管]\*\*\*\* 中，以滑鼠右鍵按一下 [參考]\*\*\*\* 節點，然後按一下 [加入參考]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e44a8-111">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2. <span data-ttu-id="e44a8-112">在 [.NET Framework]\*\*\*\* 索引標籤上，捲動到 [System.dll]\*\*\*\*，然後按一下 [選取]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e44a8-112">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3. <span data-ttu-id="e44a8-113">捲動到 [System.ServiceProcess.dll]\*\*\*\*，然後按一下 [選取]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e44a8-113">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4. <span data-ttu-id="e44a8-114">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e44a8-114">Click **OK**.</span></span>  
  
2. <span data-ttu-id="e44a8-115">加入類別，並將它設定為繼承自 <xref:System.ServiceProcess.ServiceBase>：</span><span class="sxs-lookup"><span data-stu-id="e44a8-115">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="e44a8-116">加入下列程式碼來設定您的服務類別：</span><span class="sxs-lookup"><span data-stu-id="e44a8-116">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="e44a8-117">為類別建立 `Main` 方法，並使用它來定義類別將包含的服務；`userService1` 是類別的名稱：</span><span class="sxs-lookup"><span data-stu-id="e44a8-117">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="e44a8-118">覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法，並定義您想要在啟動服務時發生的任何處理。</span><span class="sxs-lookup"><span data-stu-id="e44a8-118">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="e44a8-119">覆寫您想要定義自訂處理的其他任何方法，並撰寫程式碼來判斷服務應該在每個案例中採取的動作。</span><span class="sxs-lookup"><span data-stu-id="e44a8-119">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="e44a8-120">為服務應用程式加入必要的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="e44a8-120">Add the necessary installers for your service application.</span></span> <span data-ttu-id="e44a8-121">如需詳細資訊，請參閱[如何：將安裝程式加入服務應用程式](how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="e44a8-121">For more information, see [How to: Add Installers to Your Service Application](how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="e44a8-122">從 [建置]\*\*\*\* 功能表選取 [建置方案]\*\*\*\*，以建置您的專案。</span><span class="sxs-lookup"><span data-stu-id="e44a8-122">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e44a8-123">請勿按 F5 執行您的專案，您無法透過這個方法來執行服務專案。</span><span class="sxs-lookup"><span data-stu-id="e44a8-123">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="e44a8-124">建立安裝專案和自訂動作來安裝您的服務。</span><span class="sxs-lookup"><span data-stu-id="e44a8-124">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="e44a8-125">如需範例，請參閱[逐步解說：在元件設計工具中建立 Windows 服務應用程式](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="e44a8-125">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="e44a8-126">安裝服務。</span><span class="sxs-lookup"><span data-stu-id="e44a8-126">Install the service.</span></span> <span data-ttu-id="e44a8-127">如需詳細資訊，請參閱 [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e44a8-127">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e44a8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e44a8-128">See also</span></span>

- [<span data-ttu-id="e44a8-129">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="e44a8-129">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="e44a8-130">作法：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="e44a8-130">How to: Create Windows Services</span></span>](how-to-create-windows-services.md)
- [<span data-ttu-id="e44a8-131">作法：將安裝程式新增至服務應用程式</span><span class="sxs-lookup"><span data-stu-id="e44a8-131">How to: Add Installers to Your Service Application</span></span>](how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="e44a8-132">作法：記錄關於服務的資訊</span><span class="sxs-lookup"><span data-stu-id="e44a8-132">How to: Log Information About Services</span></span>](how-to-log-information-about-services.md)
- [<span data-ttu-id="e44a8-133">逐步解說：在元件設計工具中建立 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="e44a8-133">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
