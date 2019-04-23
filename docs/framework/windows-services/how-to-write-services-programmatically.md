---
title: 作法：以程式設計方式撰寫服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- services, creating
- Windows Service applications, creating
ms.assetid: 3abbb2ec-78d2-41e6-b9f9-6662d4e2cdc7
author: ghogen
ms.openlocfilehash: baa7655481c24ebe96b76a0accbff63b6965a021
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328422"
---
# <a name="how-to-write-services-programmatically"></a><span data-ttu-id="991b4-102">作法：以程式設計方式撰寫服務</span><span class="sxs-lookup"><span data-stu-id="991b4-102">How to: Write Services Programmatically</span></span>
<span data-ttu-id="991b4-103">如果您選擇不使用 Windows 服務專案範本，則可以藉由自行設定繼承和其他基礎結構元素來撰寫自己的服務。</span><span class="sxs-lookup"><span data-stu-id="991b4-103">If you choose not to use the Windows Service project template, you can write your own services by setting up the inheritance and other infrastructure elements yourself.</span></span> <span data-ttu-id="991b4-104">當您以程式設計方式建立服務時，必須執行範本會為您處理的數個步驟：</span><span class="sxs-lookup"><span data-stu-id="991b4-104">When you create a service programmatically, you must perform several steps that the template would otherwise handle for you:</span></span>  
  
-   <span data-ttu-id="991b4-105">您必須將服務類別設定為繼承自 <xref:System.ServiceProcess.ServiceBase> 類別。</span><span class="sxs-lookup"><span data-stu-id="991b4-105">You must set up your service class to inherit from the <xref:System.ServiceProcess.ServiceBase> class.</span></span>  
  
-   <span data-ttu-id="991b4-106">您必須建立服務專案的 `Main` 方法，以定義要執行的服務並在其上呼叫 <xref:System.ServiceProcess.ServiceBase.Run%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="991b4-106">You must create a `Main` method for your service project that defines the services to run and calls the <xref:System.ServiceProcess.ServiceBase.Run%2A> method on them.</span></span>  
  
-   <span data-ttu-id="991b4-107">您必須覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 程序，並填入任何要執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="991b4-107">You must override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> procedures and fill in any code you want them to run.</span></span>  
  
### <a name="to-write-a-service-programmatically"></a><span data-ttu-id="991b4-108">以程式設計方式撰寫服務</span><span class="sxs-lookup"><span data-stu-id="991b4-108">To write a service programmatically</span></span>  
  
1. <span data-ttu-id="991b4-109">依照下列步驟來建立空白的專案，並建立必要命名空間的參考：</span><span class="sxs-lookup"><span data-stu-id="991b4-109">Create an empty project and create a reference to the necessary namespaces by following these steps:</span></span>  
  
    1.  <span data-ttu-id="991b4-110">在 [方案總管] 中，以滑鼠右鍵按一下 [參考] 節點，然後按一下 [加入參考]。</span><span class="sxs-lookup"><span data-stu-id="991b4-110">In **Solution Explorer**, right-click the **References** node and click **Add Reference**.</span></span>  
  
    2.  <span data-ttu-id="991b4-111">在 [.NET Framework] 索引標籤上，捲動到 [System.dll]，然後按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="991b4-111">On the **.NET Framework** tab, scroll to **System.dll** and click **Select**.</span></span>  
  
    3.  <span data-ttu-id="991b4-112">捲動到 [System.ServiceProcess.dll]，然後按一下 [選取]。</span><span class="sxs-lookup"><span data-stu-id="991b4-112">Scroll to **System.ServiceProcess.dll** and click **Select**.</span></span>  
  
    4.  <span data-ttu-id="991b4-113">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="991b4-113">Click **OK**.</span></span>  
  
2. <span data-ttu-id="991b4-114">加入類別，並將它設定為繼承自 <xref:System.ServiceProcess.ServiceBase>：</span><span class="sxs-lookup"><span data-stu-id="991b4-114">Add a class and configure it to inherit from <xref:System.ServiceProcess.ServiceBase>:</span></span>  
  
     [!code-csharp[VbRadconService#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#7)]
     [!code-vb[VbRadconService#7](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#7)]  
  
3. <span data-ttu-id="991b4-115">加入下列程式碼來設定您的服務類別：</span><span class="sxs-lookup"><span data-stu-id="991b4-115">Add the following code to configure your service class:</span></span>  
  
     [!code-csharp[VbRadconService#8](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#8)]
     [!code-vb[VbRadconService#8](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#8)]  
  
4. <span data-ttu-id="991b4-116">為類別建立 `Main` 方法，並使用它來定義類別將包含的服務；`userService1` 是類別的名稱：</span><span class="sxs-lookup"><span data-stu-id="991b4-116">Create a `Main` method for your class, and use it to define the service your class will contain; `userService1` is the name of the class:</span></span>  
  
     [!code-csharp[VbRadconService#9](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#9)]
     [!code-vb[VbRadconService#9](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#9)]  
  
5. <span data-ttu-id="991b4-117">覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法，並定義您想要在啟動服務時發生的任何處理。</span><span class="sxs-lookup"><span data-stu-id="991b4-117">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method, and define any processing you want to occur when your service is started.</span></span>  
  
     [!code-csharp[VbRadconService#10](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#10)]
     [!code-vb[VbRadconService#10](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#10)]  
  
6. <span data-ttu-id="991b4-118">覆寫您想要定義自訂處理的其他任何方法，並撰寫程式碼來判斷服務應該在每個案例中採取的動作。</span><span class="sxs-lookup"><span data-stu-id="991b4-118">Override any other methods you want to define custom processing for, and write code to determine the actions the service should take in each case.</span></span>  
  
7. <span data-ttu-id="991b4-119">為服務應用程式加入必要的安裝程式。</span><span class="sxs-lookup"><span data-stu-id="991b4-119">Add the necessary installers for your service application.</span></span> <span data-ttu-id="991b4-120">如需詳細資訊，請參閱[如何：將安裝程式新增至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。</span><span class="sxs-lookup"><span data-stu-id="991b4-120">For more information, see [How to: Add Installers to Your Service Application](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).</span></span>  
  
8. <span data-ttu-id="991b4-121">從 [建置] 功能表選取 [建置方案]，以建置您的專案。</span><span class="sxs-lookup"><span data-stu-id="991b4-121">Build your project by selecting **Build Solution** from the **Build** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="991b4-122">請勿按 F5 執行您的專案，您無法透過這個方法來執行服務專案。</span><span class="sxs-lookup"><span data-stu-id="991b4-122">Do not press F5 to run your project — you cannot run a service project in this way.</span></span>  
  
9. <span data-ttu-id="991b4-123">建立安裝專案和自訂動作來安裝您的服務。</span><span class="sxs-lookup"><span data-stu-id="991b4-123">Create a setup project and the custom actions to install your service.</span></span> <span data-ttu-id="991b4-124">如需範例，請參閱[逐步解說：在元件設計工具中建立 Windows 服務應用程式](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)。</span><span class="sxs-lookup"><span data-stu-id="991b4-124">For an example, see [Walkthrough: Creating a Windows Service Application in the Component Designer](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md).</span></span>  
  
10. <span data-ttu-id="991b4-125">安裝服務。</span><span class="sxs-lookup"><span data-stu-id="991b4-125">Install the service.</span></span> <span data-ttu-id="991b4-126">如需詳細資訊，請參閱[如何：安裝和解除安裝服務](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)。</span><span class="sxs-lookup"><span data-stu-id="991b4-126">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="991b4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="991b4-127">See also</span></span>

- [<span data-ttu-id="991b4-128">Windows 服務應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="991b4-128">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="991b4-129">作法：建立 Windows 服務</span><span class="sxs-lookup"><span data-stu-id="991b4-129">How to: Create Windows Services</span></span>](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [<span data-ttu-id="991b4-130">作法：將安裝程式新增至服務應用程式</span><span class="sxs-lookup"><span data-stu-id="991b4-130">How to: Add Installers to Your Service Application</span></span>](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
- [<span data-ttu-id="991b4-131">作法：記錄關於服務的資訊</span><span class="sxs-lookup"><span data-stu-id="991b4-131">How to: Log Information About Services</span></span>](../../../docs/framework/windows-services/how-to-log-information-about-services.md)
- [<span data-ttu-id="991b4-132">逐步解說：在元件設計工具中建立 Windows 服務應用程式</span><span class="sxs-lookup"><span data-stu-id="991b4-132">Walkthrough: Creating a Windows Service Application in the Component Designer</span></span>](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
