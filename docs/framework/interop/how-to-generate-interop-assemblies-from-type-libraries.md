---
title: 作法：從型別程式庫產生 Interop 組件
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- Type Library Importer
- type libraries
- COM interop, importing type library
ms.assetid: 4afd40c3-68f2-41c5-8ec1-4951bc148b9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a3ee82a9091f0caeee010ec79632ce703efb589
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338835"
---
# <a name="how-to-generate-interop-assemblies-from-type-libraries"></a><span data-ttu-id="bf369-102">作法：從型別程式庫產生 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="bf369-102">How to: Generate Interop Assemblies from Type Libraries</span></span>
<span data-ttu-id="bf369-103">[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 是一種命令列工具，可將 COM 類型程式庫中包含的 Coclass 和介面轉換為中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bf369-103">The [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) is a command-line tool that converts the coclasses and interfaces contained in a COM type library to metadata.</span></span> <span data-ttu-id="bf369-104">這個工具會自動為類型資訊建立 Interop 組件和命名空間。</span><span class="sxs-lookup"><span data-stu-id="bf369-104">This tool creates an interop assembly and namespace for the type information automatically.</span></span> <span data-ttu-id="bf369-105">當類別的中繼資料可供使用之後，Managed 用戶端就可以建立 COM 類型的執行個體並呼叫其方法，就如同它是 .NET 執行個體一樣。</span><span class="sxs-lookup"><span data-stu-id="bf369-105">After the metadata of a class is available, managed clients can create instances of the COM type and call its methods, just as if it were a .NET instance.</span></span> <span data-ttu-id="bf369-106">Tlbimp.exe 會一次將整個型別程式庫轉換為中繼資料，而且不能為型別程式庫中定義的類型子集產生類型資訊。</span><span class="sxs-lookup"><span data-stu-id="bf369-106">Tlbimp.exe converts an entire type library to metadata at once and cannot generate type information for a subset of the types defined in a type library.</span></span>  
  
### <a name="to-generate-an-interop-assembly-from-a-type-library"></a><span data-ttu-id="bf369-107">從型別程式庫產生 Interop 組件</span><span class="sxs-lookup"><span data-stu-id="bf369-107">To generate an interop assembly from a type library</span></span>  
  
1. <span data-ttu-id="bf369-108">請使用以下命令：</span><span class="sxs-lookup"><span data-stu-id="bf369-108">Use the following command:</span></span>  
  
     <span data-ttu-id="bf369-109">**tlbimp** \<*type-library-file*></span><span class="sxs-lookup"><span data-stu-id="bf369-109">**tlbimp** \<*type-library-file*></span></span>  
  
     <span data-ttu-id="bf369-110">新增 **/out:** 參數會產生已變更名稱的 Interop 組件，例如 LOANLib.dll。</span><span class="sxs-lookup"><span data-stu-id="bf369-110">Adding the **/out:** switch produces an interop assembly with an altered name, such as LOANLib.dll.</span></span> <span data-ttu-id="bf369-111">變更 Interop 組件的名稱有助於與原始 COM DLL 區別，且可避免因為具有重複名稱而產生的問題。</span><span class="sxs-lookup"><span data-stu-id="bf369-111">Altering the interop assembly name can help distinguish it from the original COM DLL and prevent problems that can occur from having duplicate names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf369-112">範例</span><span class="sxs-lookup"><span data-stu-id="bf369-112">Example</span></span>  
 <span data-ttu-id="bf369-113">下列命令會在 `Loanlib` 命名空間中產生 Loanlib.dll 組件。</span><span class="sxs-lookup"><span data-stu-id="bf369-113">The following command produces the Loanlib.dll assembly in the `Loanlib` namespace.</span></span>  
  
```  
tlbimp Loanlib.tlb  
```  
  
 <span data-ttu-id="bf369-114">下列命令會產生已變更名稱 (LOANLib.dll) 的 Interop 組件。</span><span class="sxs-lookup"><span data-stu-id="bf369-114">The following command produces an interop assembly with an altered name (LOANLib.dll).</span></span>  
  
```  
tlbimp LoanLib.tlb /out: LOANLib.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf369-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf369-115">See also</span></span>

- [<span data-ttu-id="bf369-116">匯入類型程式庫做為組件</span><span class="sxs-lookup"><span data-stu-id="bf369-116">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="bf369-117">將 COM 元件公開給 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bf369-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)
