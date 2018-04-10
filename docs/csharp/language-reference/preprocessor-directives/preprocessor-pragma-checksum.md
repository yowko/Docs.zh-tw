---
title: '#pragma 總和檢查碼 (C# 參考)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0604a559be25c300fcdc6041975306b465fc595f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="24785-102">#pragma 總和檢查碼 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="24785-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="24785-103">產生來源檔案的總和檢查碼協助偵錯[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]頁面。</span><span class="sxs-lookup"><span data-stu-id="24785-103">Generates checksums for source files to aid with debugging [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24785-104">語法</span><span class="sxs-lookup"><span data-stu-id="24785-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24785-105">參數</span><span class="sxs-lookup"><span data-stu-id="24785-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="24785-106">需要監視是否有變更或更新的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="24785-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="24785-107">檔案的全域唯一識別碼 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="24785-107">The Globally Unique Identifier (GUID) for the file.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="24785-108">代表總和檢查碼位元組的十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="24785-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="24785-109">必須是偶數的十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="24785-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="24785-110">奇數的數字會導致編譯時期警告，並且忽略指示詞。</span><span class="sxs-lookup"><span data-stu-id="24785-110">An odd number of digits results in a compile-time warning, and the directive are  ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24785-111">備註</span><span class="sxs-lookup"><span data-stu-id="24785-111">Remarks</span></span>  
 <span data-ttu-id="24785-112">Visual Studio 偵錯工具會使用總和檢查碼來確定一定會找到正確的來源。</span><span class="sxs-lookup"><span data-stu-id="24785-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="24785-113">編譯器會計算來源檔案的總和檢查碼，然後將輸出發至程式資料庫 (PDB) 檔案。</span><span class="sxs-lookup"><span data-stu-id="24785-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="24785-114">然後偵錯工具會使用 PDB 比較總和檢查碼計算來源檔案。</span><span class="sxs-lookup"><span data-stu-id="24785-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="24785-115">這個解決方案不適用於 [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] 專案，因為計算過的總和檢查碼適合產生的來源檔案，不是 .aspx 檔案。</span><span class="sxs-lookup"><span data-stu-id="24785-115">This solution does not work for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="24785-116">若要解決這個問題，`#pragma checksum` 會為 [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] 頁面提供總和檢查碼支援。</span><span class="sxs-lookup"><span data-stu-id="24785-116">To address this problem, `#pragma checksum` provides checksum support for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
 <span data-ttu-id="24785-117">當您在 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 中建立 [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] 專案時，產生的來源檔案會包含 .aspx 檔案的總和檢查碼，來源於此產生。</span><span class="sxs-lookup"><span data-stu-id="24785-117">When you create an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] project in [!INCLUDE[csprcs](~/includes/csprcs-md.md)], the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="24785-118">接著編譯器會將這項資訊寫入 PDB 檔案中。</span><span class="sxs-lookup"><span data-stu-id="24785-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="24785-119">如果編譯器在檔案中未遇到任何 `#pragma checksum` 指示詞，它會計算總和檢查碼並將值寫入 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="24785-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24785-120">範例</span><span class="sxs-lookup"><span data-stu-id="24785-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="24785-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24785-121">See Also</span></span>  
 [<span data-ttu-id="24785-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="24785-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="24785-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="24785-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="24785-124">C# 前置處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="24785-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
