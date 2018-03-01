---
title: "Windows Form 的應用程式設定"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ClientApplicationSettings
helpviewer_keywords:
- application settings [Windows Forms]
- Windows Forms, application settings
ms.assetid: 64090a34-8556-4904-8ea0-20efe9f8c886
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 63248009497152a41a6313a50ed6e7544ac62cbe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-for-windows-forms"></a><span data-ttu-id="71636-102">Windows Form 的應用程式設定</span><span class="sxs-lookup"><span data-stu-id="71636-102">Application Settings for Windows Forms</span></span>
<span data-ttu-id="71636-103">Windows Form 的應用程式設定功能可讓您輕鬆地在用戶端上建立、儲存及維護自訂應用程式和使用者偏好設定。</span><span class="sxs-lookup"><span data-stu-id="71636-103">The Applications Settings feature of Windows Forms makes it easy to create, store, and maintain custom application and user preferences on the client.</span></span> <span data-ttu-id="71636-104">利用應用程式設定，您不只可以儲存應用程式資料 (例如資料庫連接字串)，也可以儲存使用者專屬資料 (例如工具列位置和最近使用的清單)。</span><span class="sxs-lookup"><span data-stu-id="71636-104">With Application Settings, you can store not only application data such as database connection strings, but also user-specific data, such as toolbar positions and most-recently used lists.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71636-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="71636-105">In This Section</span></span>  
 [<span data-ttu-id="71636-106">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="71636-106">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)  
 <span data-ttu-id="71636-107">討論如何代表您的應用程式和使用者來建立及儲存設定資料。</span><span class="sxs-lookup"><span data-stu-id="71636-107">Discusses how to create and store settings data on behalf of your application and your users.</span></span>  
  
 [<span data-ttu-id="71636-108">應用程式設定架構</span><span class="sxs-lookup"><span data-stu-id="71636-108">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)  
 <span data-ttu-id="71636-109">描述應用程式設定功能的運作方式，並且瀏覽架構的進階功能 (例如已群組的設定和設定索引鍵)。</span><span class="sxs-lookup"><span data-stu-id="71636-109">Describes how the Application Settings feature works, and explores advanced features of the architecture such as grouped settings and settings keys.</span></span>  
  
 [<span data-ttu-id="71636-110">應用程式設定屬性</span><span class="sxs-lookup"><span data-stu-id="71636-110">Application Settings Attributes</span></span>](~/docs/framework/winforms/advanced/application-settings-attributes.md)  
 <span data-ttu-id="71636-111">列出並描述可套用至應用程式設定包裝函式類別或其設定屬性 (Property) 的屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="71636-111">Lists and describes the attributes that can be applied to an application settings wrapper class or its settings properties.</span></span>  
  
 [<span data-ttu-id="71636-112">自訂控制項的應用程式設定</span><span class="sxs-lookup"><span data-stu-id="71636-112">Application Settings for Custom Controls</span></span>](~/docs/framework/winforms/advanced/application-settings-for-custom-controls.md)  
 <span data-ttu-id="71636-113">討論在第三方應用程式中裝載時，要讓自訂控制項能夠保存應用程式設定所須執行的作業。</span><span class="sxs-lookup"><span data-stu-id="71636-113">Discusses what must be done to give your custom controls the ability to persist application settings when hosted in third-party applications.</span></span>  
  
 [<span data-ttu-id="71636-114">如何：建立應用程式設定</span><span class="sxs-lookup"><span data-stu-id="71636-114">How to: Create Application Settings</span></span>](~/docs/framework/winforms/advanced/how-to-create-application-settings.md)  
 <span data-ttu-id="71636-115">示範如何建立新的應用程式設定，這些設定會在兩個應用程式工作階段之間保存。</span><span class="sxs-lookup"><span data-stu-id="71636-115">Demonstrates creating new application settings that are persisted between application sessions.</span></span>  
  
 [<span data-ttu-id="71636-116">操作說明：驗證應用程式設定</span><span class="sxs-lookup"><span data-stu-id="71636-116">How to: Validate Application Settings</span></span>](~/docs/framework/winforms/advanced/how-to-validate-application-settings.md)  
 <span data-ttu-id="71636-117">示範如何在保存應用程式設定之前先行驗證。</span><span class="sxs-lookup"><span data-stu-id="71636-117">Demonstrates validating application settings before they are persisted.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="71636-118">相關主題</span><span class="sxs-lookup"><span data-stu-id="71636-118">Related topics</span></span>

<span data-ttu-id="71636-119">[Windows Form 的組態區段](../../../../docs/framework/configure-apps/file-schema/winforms/index.md)  </span><span class="sxs-lookup"><span data-stu-id="71636-119">[Windows Forms Configuration Section](../../../../docs/framework/configure-apps/file-schema/winforms/index.md)  </span></span>  
<span data-ttu-id="71636-120">文件中 Windows Form 應用程式從.NET Framework 4.7 支援啟用高 DPI 的設定。</span><span class="sxs-lookup"><span data-stu-id="71636-120">Documents the settings to enable High DPI support in Windows Forms Application starting with the .NET Framework 4.7.</span></span>

## <a name="see-also"></a><span data-ttu-id="71636-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71636-121">See also</span></span>  
  
[<span data-ttu-id="71636-122">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="71636-122">Windows Forms</span></span>](../index.md)
