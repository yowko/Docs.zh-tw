---
title: Windows Form 的應用程式設定
ms.date: 04/07/2017
f1_keywords:
- ClientApplicationSettings
helpviewer_keywords:
- application settings [Windows Forms]
- Windows Forms, application settings
ms.assetid: 64090a34-8556-4904-8ea0-20efe9f8c886
ms.openlocfilehash: 0cac4433ec9fe54721752c63d2b3b37f9d874c19
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719308"
---
# <a name="application-settings-for-windows-forms"></a><span data-ttu-id="70a8d-102">Windows Form 的應用程式設定</span><span class="sxs-lookup"><span data-stu-id="70a8d-102">Application Settings for Windows Forms</span></span>
<span data-ttu-id="70a8d-103">Windows Form 的應用程式設定功能可讓您輕鬆地在用戶端上建立、儲存及維護自訂應用程式和使用者偏好設定。</span><span class="sxs-lookup"><span data-stu-id="70a8d-103">The Applications Settings feature of Windows Forms makes it easy to create, store, and maintain custom application and user preferences on the client.</span></span> <span data-ttu-id="70a8d-104">利用應用程式設定，您不只可以儲存應用程式資料 (例如資料庫連接字串)，也可以儲存使用者專屬資料 (例如工具列位置和最近使用的清單)。</span><span class="sxs-lookup"><span data-stu-id="70a8d-104">With Application Settings, you can store not only application data such as database connection strings, but also user-specific data, such as toolbar positions and most-recently used lists.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70a8d-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="70a8d-105">In This Section</span></span>  
 [<span data-ttu-id="70a8d-106">應用程式設定概觀</span><span class="sxs-lookup"><span data-stu-id="70a8d-106">Application Settings Overview</span></span>](~/docs/framework/winforms/advanced/application-settings-overview.md)  
 <span data-ttu-id="70a8d-107">討論如何代表您的應用程式和使用者來建立及儲存設定資料。</span><span class="sxs-lookup"><span data-stu-id="70a8d-107">Discusses how to create and store settings data on behalf of your application and your users.</span></span>  
  
 [<span data-ttu-id="70a8d-108">應用程式設定架構</span><span class="sxs-lookup"><span data-stu-id="70a8d-108">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)  
 <span data-ttu-id="70a8d-109">描述應用程式設定功能的運作方式，並且瀏覽架構的進階功能 (例如已群組的設定和設定索引鍵)。</span><span class="sxs-lookup"><span data-stu-id="70a8d-109">Describes how the Application Settings feature works, and explores advanced features of the architecture such as grouped settings and settings keys.</span></span>  
  
 [<span data-ttu-id="70a8d-110">應用程式設定屬性</span><span class="sxs-lookup"><span data-stu-id="70a8d-110">Application Settings Attributes</span></span>](~/docs/framework/winforms/advanced/application-settings-attributes.md)  
 <span data-ttu-id="70a8d-111">列出並描述可套用至應用程式設定包裝函式類別或其設定屬性 (Property) 的屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="70a8d-111">Lists and describes the attributes that can be applied to an application settings wrapper class or its settings properties.</span></span>  
  
 [<span data-ttu-id="70a8d-112">Application Settings for Custom Controls</span><span class="sxs-lookup"><span data-stu-id="70a8d-112">Application Settings for Custom Controls</span></span>](~/docs/framework/winforms/advanced/application-settings-for-custom-controls.md)  
 <span data-ttu-id="70a8d-113">討論在第三方應用程式中裝載時，要讓自訂控制項能夠保存應用程式設定所須執行的作業。</span><span class="sxs-lookup"><span data-stu-id="70a8d-113">Discusses what must be done to give your custom controls the ability to persist application settings when hosted in third-party applications.</span></span>  
  
 [<span data-ttu-id="70a8d-114">如何：建立應用程式設定</span><span class="sxs-lookup"><span data-stu-id="70a8d-114">How to: Create Application Settings</span></span>](~/docs/framework/winforms/advanced/how-to-create-application-settings.md)  
 <span data-ttu-id="70a8d-115">示範如何建立新的應用程式設定，這些設定會在兩個應用程式工作階段之間保存。</span><span class="sxs-lookup"><span data-stu-id="70a8d-115">Demonstrates creating new application settings that are persisted between application sessions.</span></span>  
  
 [<span data-ttu-id="70a8d-116">如何：驗證應用程式設定</span><span class="sxs-lookup"><span data-stu-id="70a8d-116">How to: Validate Application Settings</span></span>](~/docs/framework/winforms/advanced/how-to-validate-application-settings.md)  
 <span data-ttu-id="70a8d-117">示範如何在保存應用程式設定之前先行驗證。</span><span class="sxs-lookup"><span data-stu-id="70a8d-117">Demonstrates validating application settings before they are persisted.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="70a8d-118">相關主題</span><span class="sxs-lookup"><span data-stu-id="70a8d-118">Related topics</span></span>

<span data-ttu-id="70a8d-119">[Windows Forms 組態區段](../../configure-apps/file-schema/winforms/index.md)  </span><span class="sxs-lookup"><span data-stu-id="70a8d-119">[Windows Forms Configuration Section](../../configure-apps/file-schema/winforms/index.md)  </span></span>  
<span data-ttu-id="70a8d-120">文件的設定，以啟用高 DPI 支援從.NET Framework 4.7 開始的 Windows Forms 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="70a8d-120">Documents the settings to enable High DPI support in Windows Forms Application starting with the .NET Framework 4.7.</span></span>

## <a name="see-also"></a><span data-ttu-id="70a8d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70a8d-121">See also</span></span>

- [<span data-ttu-id="70a8d-122">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="70a8d-122">Windows Forms</span></span>](../index.md)
