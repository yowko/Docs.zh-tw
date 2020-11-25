---
title: Tlbexp Helper 函式 (Unmanaged API 參考)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
ms.openlocfilehash: 9386918f3574720d90bda7e8da592fa0c91160e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708240"
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="3066a-102">Tlbexp Helper 函式 (Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="3066a-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>

<span data-ttu-id="3066a-103">[型別程式庫匯出工具](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) 會載入名為 TlbRef.dll 的˙動態連結程式庫。</span><span class="sxs-lookup"><span data-stu-id="3066a-103">The [Type Library Exporter tool](../../tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="3066a-104">此 DLL 包含兩個協助程式函式，以及匯出工具在「組件-至-型別-程式庫」轉換程序期間使用的介面。</span><span class="sxs-lookup"><span data-stu-id="3066a-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3066a-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="3066a-105">In This Section</span></span>  

 [<span data-ttu-id="3066a-106">GetTypeLibInfo 函式</span><span class="sxs-lookup"><span data-stu-id="3066a-106">GetTypeLibInfo Function</span></span>](gettypelibinfo-function.md)  
 <span data-ttu-id="3066a-107">提供型別程式庫的當地語系化與作業系統資訊。</span><span class="sxs-lookup"><span data-stu-id="3066a-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="3066a-108">LoadTypeLibWithResolver 函式</span><span class="sxs-lookup"><span data-stu-id="3066a-108">LoadTypeLibWithResolver Function</span></span>](loadtypelibwithresolver-function.md)  
 <span data-ttu-id="3066a-109">透過使用 [ITypeLibResolver 介面](itypelibresolver-interface.md)的實載入型別程式庫，以解析任何參考的型別程式庫。</span><span class="sxs-lookup"><span data-stu-id="3066a-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="3066a-110">ITypeLibResolver 介面</span><span class="sxs-lookup"><span data-stu-id="3066a-110">ITypeLibResolver Interface</span></span>](itypelibresolver-interface.md)  
 <span data-ttu-id="3066a-111">提供 [ResolveTypeLib 方法](resolvetypelib-method.md)，此方法會傳回型別程式庫的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="3066a-111">Provides the [ResolveTypeLib method](resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
