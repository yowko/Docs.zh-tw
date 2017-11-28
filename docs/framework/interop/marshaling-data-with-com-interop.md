---
title: "使用 COM Interop 封送處理資料"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2def27790a1727bda524b8c14a93f7b78127a569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="marshaling-data-with-com-interop"></a><span data-ttu-id="8b2ac-102">使用 COM Interop 封送處理資料</span><span class="sxs-lookup"><span data-stu-id="8b2ac-102">Marshaling Data with COM Interop</span></span>
<span data-ttu-id="8b2ac-103">COM Interop 同時提供使用來自 Managed 程式碼之 COM 物件的支援和公開 Managed 物件給 COM 的支援。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-103">COM interop provides support for both using COM objects from managed code and exposing managed objects to COM.</span></span> <span data-ttu-id="8b2ac-104">廣泛支援封送處理資料至 COM 或對來自 COM 的資料封送處理，幾乎一律會提供正確的封送處理行為。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-104">Support for marshaling data to and from COM is extensive and almost always provides the correct marshaling behavior.</span></span>  
  
 <span data-ttu-id="8b2ac-105">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 包含下列的 COM Interop 工具：</span><span class="sxs-lookup"><span data-stu-id="8b2ac-105">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] includes the following COM interop tools:</span></span>  
  
-   <span data-ttu-id="8b2ac-106">[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)，這會將 COM 型別程式庫轉換成 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-106">[Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md), which converts a COM type library to an interop assembly.</span></span> <span data-ttu-id="8b2ac-107">從這個組件中，Interop 封送處理服務會產生包裝函式，在 Managed 和 Unmanaged 記憶體之間執行資料封送處理。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-107">From this assembly, the interop marshaling service generates wrappers that perform data marshaling between managed and unmanaged memory.</span></span>  
  
-   <span data-ttu-id="8b2ac-108">[型別程式庫匯出工具 (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)，這會從組件產生 COM 型別程式庫，並產生在方法呼叫期間執行封送處理的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-108">[Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which produces a COM type library from an assembly and generates a wrapper that performs marshaling during method calls.</span></span>  
  
 <span data-ttu-id="8b2ac-109">下列各節將說明您可以 （或必須） 提供具有其他類型資訊的封送處理器時，自訂 interop 包裝函式的處理程序的主題連結。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-109">The following sections link to topics that describe the processes for customizing interop wrappers when you can (or must) supply the marshaler with additional type information.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b2ac-110">本章節內容</span><span class="sxs-lookup"><span data-stu-id="8b2ac-110">In This Section</span></span>  
<span data-ttu-id="8b2ac-111">[如何： 手動建立包裝函式](how-to-create-wrappers-manually.md) </span><span class="sxs-lookup"><span data-stu-id="8b2ac-111">[How to: Create Wrappers Manually](how-to-create-wrappers-manually.md) </span></span>  
<span data-ttu-id="8b2ac-112">描述如何在 managed 的原始程式碼中手動建立 COM 包裝函式。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-112">Describes how to create a COM wrapper manually in managed source code.</span></span> 
 
 [<span data-ttu-id="8b2ac-113">如何：將 Managed 程式碼 DCOM 移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="8b2ac-113">How to: Migrate Managed-Code DCOM to WCF</span></span>](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 <span data-ttu-id="8b2ac-114">描述如何將 managed 的 DCOM 程式碼移轉至 WCF 的最安全的解決方案。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-114">Describes how to migrate managed DCOM code to WCF for the most secure solution.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8b2ac-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="8b2ac-115">Related Sections</span></span>  
 <span data-ttu-id="8b2ac-116">[COM 資料類型](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b2ac-116">[COM Data Types](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8b2ac-117">提供對應的 Managed 和 Unmanaged 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-117">Provides corresponding managed and unmanaged data types.</span></span>  
  
 <span data-ttu-id="8b2ac-118">[自訂 COM 可呼叫包裝函式](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b2ac-118">[Customizing COM Callable Wrappers](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8b2ac-119">描述如何明確封送處理資料型別使用<xref:System.Runtime.InteropServices.MarshalAsAttribute>在設計階段屬性。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-119">Describes how to explicitly marshal data types using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute at design time.</span></span>  
  
 <span data-ttu-id="8b2ac-120">[自訂執行階段可呼叫包裝函式](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b2ac-120">[Customizing Runtime Callable Wrappers](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8b2ac-121">描述如何調整 Interop 組件中的類型封送處理行為，以及描述如何以手動方式定義 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-121">Describes how to adjust the marshaling behavior of types in an interop assembly and how to define COM types manually.</span></span>  
  
 <span data-ttu-id="8b2ac-122">[進階 COM 互通性](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b2ac-122">[Advanced COM Interoperability](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8b2ac-123">提供有關將 COM 元件納入 .NET Framework 應用程式的詳細資訊連結。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-123">Provides links to more information about incorporating COM components into your .NET Framework application.</span></span>  
  
 <span data-ttu-id="8b2ac-124">[組件至型別程式庫轉換的摘要](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b2ac-124">[Assembly to Type Library Conversion Summary](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8b2ac-125">描述組件至類型程式庫匯出轉換的程序。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-125">Describes the assembly to type library export conversion process.</span></span>  
  
 <span data-ttu-id="8b2ac-126">[型別程式庫至組件轉換的摘要](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b2ac-126">[Type Library to Assembly Conversion Summary](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8b2ac-127">描述類型程式庫至組件匯入轉換的程序。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-127">Describes the type library to assembly import conversion process.</span></span>  
  
 <span data-ttu-id="8b2ac-128">[使用泛型型別互通](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="8b2ac-128">[Interoperating Using Generic Types](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)</span></span>  
 <span data-ttu-id="8b2ac-129">描述使用泛型類型來取得 COM 互通性時所支援的動作。</span><span class="sxs-lookup"><span data-stu-id="8b2ac-129">Describes which actions are supported when using generic types for COM interoperability.</span></span>
