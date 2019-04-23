---
title: 作法：參考 COM 的 .NET 類型
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e033ba4b3b98367452b355363058adc7f1a5887
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198396"
---
# <a name="how-to-reference-net-types-from-com"></a><span data-ttu-id="7bb66-102">作法：參考 COM 的 .NET 類型</span><span class="sxs-lookup"><span data-stu-id="7bb66-102">How to: Reference .NET Types from COM</span></span>
<span data-ttu-id="7bb66-103">從用戶端和伺服器程式碼的觀點來看，COM 和 .NET Framework 之間的差異大部分是無形的。</span><span class="sxs-lookup"><span data-stu-id="7bb66-103">From the point of view of client and server code, the differences between COM and the .NET Framework are largely invisible.</span></span> <span data-ttu-id="7bb66-104">Microsoft Visual Basic 用戶端可以在物件瀏覽器中檢視 .NET 物件，這會公開物件方法和語法、屬性及欄位，完全如同它是任何其他 COM 物件一樣。</span><span class="sxs-lookup"><span data-stu-id="7bb66-104">Microsoft Visual Basic clients can view a .NET object in the object browser, which exposes the object methods and syntax, properties, and fields exactly as if it were any other COM object.</span></span>  
  
 <span data-ttu-id="7bb66-105">匯入型別程式庫的程序對 C++ 的用戶端而言稍嫌複雜，不過您可以使用相同的工具，將中繼資料匯出至 COM 類型程式庫。</span><span class="sxs-lookup"><span data-stu-id="7bb66-105">The process for importing a type library is slightly more complicated for C++ clients, although you use the same tools to export metadata to a COM type library.</span></span> <span data-ttu-id="7bb66-106">若要從 Unmanaged C++ 用戶端參考 .NET 物件成員，請使用 **#import** 指示詞參考 TLB 檔案 (使用 Tlbexp.exe 產生)。</span><span class="sxs-lookup"><span data-stu-id="7bb66-106">To reference .NET object members from an unmanaged C++ client, reference the TLB file (produced with Tlbexp.exe) with the **#import** directive.</span></span> <span data-ttu-id="7bb66-107">從 C++ 參考型別程式庫時，您必須指定 **raw_interfaces_only** 選項，或匯入基底類別程式庫 Mscorlib.tlb 中的定義。</span><span class="sxs-lookup"><span data-stu-id="7bb66-107">When referencing a type library from C++, you must either specify the **raw_interfaces_only** option or import the definitions in the base class library, Mscorlib.tlb.</span></span>  
  
### <a name="to-import-a-library"></a><span data-ttu-id="7bb66-108">匯入程式庫</span><span class="sxs-lookup"><span data-stu-id="7bb66-108">To import a library</span></span>  
  
-   <span data-ttu-id="7bb66-109">在 **#import** 指示詞中指定 **raw_interfaces_only** 選項。</span><span class="sxs-lookup"><span data-stu-id="7bb66-109">Specify the **raw_interfaces_only** option in the **#import** directive.</span></span> <span data-ttu-id="7bb66-110">例如：</span><span class="sxs-lookup"><span data-stu-id="7bb66-110">For example:</span></span>  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     <span data-ttu-id="7bb66-111">-或-</span><span class="sxs-lookup"><span data-stu-id="7bb66-111">-or-</span></span>  
  
-   <span data-ttu-id="7bb66-112">包括 Mscorlib.tlb 的 #import 指示詞。</span><span class="sxs-lookup"><span data-stu-id="7bb66-112">Include an #import directive for Mscorlib.tlb.</span></span> <span data-ttu-id="7bb66-113">例如：</span><span class="sxs-lookup"><span data-stu-id="7bb66-113">For example:</span></span>  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7bb66-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bb66-114">See also</span></span>

- [<span data-ttu-id="7bb66-115">將 .NET Framework 元件公開給 COM</span><span class="sxs-lookup"><span data-stu-id="7bb66-115">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="7bb66-116">向 COM 註冊組件</span><span class="sxs-lookup"><span data-stu-id="7bb66-116">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- [<span data-ttu-id="7bb66-117">呼叫 .NET 物件</span><span class="sxs-lookup"><span data-stu-id="7bb66-117">Calling a .NET Object</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))
- [<span data-ttu-id="7bb66-118">部署供 COM 存取的應用程式</span><span class="sxs-lookup"><span data-stu-id="7bb66-118">Deploying an Application for COM Access</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))
