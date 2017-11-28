---
title: "如何：參考 COM 的 .NET 類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f58225e41d7e09471685395dd6e2194ee5de123c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="26f28-102">如何：參考 COM 的 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="26f28-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="26f28-103">從用戶端和伺服器程式碼的觀點來看，COM 和 .NET Framework 之間的差異大部分是無形的。</span><span class="sxs-lookup"><span data-stu-id="26f28-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="26f28-104">Microsoft Visual Basic 用戶端可以在物件瀏覽器中檢視 .NET 物件，這會公開物件方法和語法、屬性及欄位，完全如同它是任何其他 COM 物件一樣。</span><span class="sxs-lookup"><span data-stu-id="26f28-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="26f28-105">匯入型別程式庫的程序對 C++ 的用戶端而言稍嫌複雜，不過您可以使用相同的工具，將中繼資料匯出至 COM 類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="26f28-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="26f28-106">若要從 Unmanaged C++ 用戶端參考 .NET 物件成員，請使用 **#import** 指示詞參考 TLB 檔案 (使用 Tlbexp.exe 產生)。</span><span class="sxs-lookup"><span data-stu-id="26f28-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="26f28-107">從 C++ 參考型別程式庫時，您必須指定 **raw_interfaces_only** 選項，或匯入基底類別程式庫 Mscorlib.tlb 中的定義。</span><span class="sxs-lookup"><span data-stu-id="26f28-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="26f28-108">匯入程式庫</span><span class="sxs-lookup"><span data-stu-id="26f28-108">To import a library</span></span>  
  
-   <span data-ttu-id="26f28-109">在 **#import** 指示詞中指定 **raw_interfaces_only** 選項。</span><span class="sxs-lookup"><span data-stu-id="26f28-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="26f28-110">例如: </span><span class="sxs-lookup"><span data-stu-id="26f28-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="26f28-111">-或-</span><span class="sxs-lookup"><span data-stu-id="26f28-111">-or-</span></span>  
  
-   <span data-ttu-id="26f28-112">包括 Mscorlib.tlb 的 #import 指示詞。</span><span class="sxs-lookup"><span data-stu-id="26f28-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="26f28-113">例如: </span><span class="sxs-lookup"><span data-stu-id="26f28-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="26f28-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26f28-114">See Also</span></span>  
 [<span data-ttu-id="26f28-115">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="26f28-115">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="26f28-116">向 COM 註冊組件</span><span class="sxs-lookup"><span data-stu-id="26f28-116">Registering Assemblies with COM</span></span>](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="26f28-117">呼叫.NET 物件</span><span class="sxs-lookup"><span data-stu-id="26f28-117">Calling a .NET Object</span></span>](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [<span data-ttu-id="26f28-118">部署供 COM 存取的應用程式</span><span class="sxs-lookup"><span data-stu-id="26f28-118">Deploying an Application for COM Access</span></span>](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)
