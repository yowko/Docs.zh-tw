---
title: "啟動設定結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
caps.latest.revision: 10
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cc014f65cec23f9ab1794d73e0f5d4f7cd5844da
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="startup-settings-schema"></a><span data-ttu-id="ab5c4-102">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ab5c4-102">Startup Settings Schema</span></span>
<span data-ttu-id="ab5c4-103">啟動設定會指定應執行應用程式之 Common Language Runtime 的版本。</span><span class="sxs-lookup"><span data-stu-id="ab5c4-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="ab5c4-104">項目</span><span class="sxs-lookup"><span data-stu-id="ab5c4-104">Element</span></span>|<span data-ttu-id="ab5c4-105">說明</span><span class="sxs-lookup"><span data-stu-id="ab5c4-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab5c4-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="ab5c4-106">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="ab5c4-107">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="ab5c4-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="ab5c4-108">使用執行階段版本 1.1 建置的應用程式應該使用 **\<supportedRuntime>** 項目。</span><span class="sxs-lookup"><span data-stu-id="ab5c4-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="ab5c4-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="ab5c4-109">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="ab5c4-110">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="ab5c4-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="ab5c4-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="ab5c4-111">\<startup></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)|<span data-ttu-id="ab5c4-112">包含 **\<requiredRuntime>** 和 **\<supportedRuntime>** 項目。</span><span class="sxs-lookup"><span data-stu-id="ab5c4-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab5c4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab5c4-113">See Also</span></span>  
 <span data-ttu-id="ab5c4-114">[組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md) </span><span class="sxs-lookup"><span data-stu-id="ab5c4-114">[Configuration File Schema](../../../../../docs/framework/configure-apps/file-schema/index.md) </span></span>  
 [<span data-ttu-id="ab5c4-115">\<PaveOver> 指定要使用哪一個執行階段版本</span><span class="sxs-lookup"><span data-stu-id="ab5c4-115">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/en-us/c376208d-980d-42b4-865b-fbe0d9cc97c2)

