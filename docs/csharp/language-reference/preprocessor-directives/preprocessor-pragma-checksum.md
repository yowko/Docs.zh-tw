---
description: '#pragma 總和檢查碼 - C# 參考'
title: '#pragma 總和檢查碼 - C# 參考'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 60c491000337fd50da217e97054e86faccb2e7d7
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137977"
---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="d946c-103">#pragma 總和檢查碼 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d946c-103">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="d946c-104">產生原始程式檔的總和檢查碼，協助偵錯 ASP.NET 頁面。</span><span class="sxs-lookup"><span data-stu-id="d946c-104">Generates checksums for source files to aid with debugging ASP.NET pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d946c-105">語法</span><span class="sxs-lookup"><span data-stu-id="d946c-105">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a><span data-ttu-id="d946c-106">參數</span><span class="sxs-lookup"><span data-stu-id="d946c-106">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="d946c-107">需要監視是否有變更或更新的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d946c-107">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="d946c-108">雜湊演算法的全域唯一識別碼 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="d946c-108">The Globally Unique Identifier (GUID) for the hash algorithm.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="d946c-109">代表總和檢查碼位元組的十六進位數字字串。</span><span class="sxs-lookup"><span data-stu-id="d946c-109">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="d946c-110">必須是偶數的十六進位數字。</span><span class="sxs-lookup"><span data-stu-id="d946c-110">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="d946c-111">奇數的數字會導致編譯時期警告，並且忽略指示詞。</span><span class="sxs-lookup"><span data-stu-id="d946c-111">An odd number of digits results in a compile-time warning, and the directive are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d946c-112">備註</span><span class="sxs-lookup"><span data-stu-id="d946c-112">Remarks</span></span>  
 <span data-ttu-id="d946c-113">Visual Studio 偵錯工具會使用總和檢查碼來確定一定會找到正確的來源。</span><span class="sxs-lookup"><span data-stu-id="d946c-113">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="d946c-114">編譯器會計算來源檔案的總和檢查碼，然後將輸出發至程式資料庫 (PDB) 檔案。</span><span class="sxs-lookup"><span data-stu-id="d946c-114">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="d946c-115">然後偵錯工具會使用 PDB 比較總和檢查碼計算來源檔案。</span><span class="sxs-lookup"><span data-stu-id="d946c-115">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="d946c-116">這個解決方案不適用於 ASP.NET 專案，因為計算過的總和檢查碼適合所產生原始程式檔而不是 .aspx 檔案。</span><span class="sxs-lookup"><span data-stu-id="d946c-116">This solution does not work for ASP.NET projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="d946c-117">若要解決這個問題，`#pragma checksum` 會為 ASP.NET 頁面提供總和檢查碼支援。</span><span class="sxs-lookup"><span data-stu-id="d946c-117">To address this problem, `#pragma checksum` provides checksum support for ASP.NET pages.</span></span>  
  
 <span data-ttu-id="d946c-118">當您在 Visual C# 中建立 ASP.NET 專案時，所產生原始程式檔會包含來源 .aspx 檔案的總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="d946c-118">When you create an ASP.NET project in Visual C#, the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="d946c-119">接著編譯器會將這項資訊寫入 PDB 檔案中。</span><span class="sxs-lookup"><span data-stu-id="d946c-119">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="d946c-120">如果編譯器在檔案中未遇到任何 `#pragma checksum` 指示詞，它會計算總和檢查碼並將值寫入 PDB 檔案。</span><span class="sxs-lookup"><span data-stu-id="d946c-120">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d946c-121">範例</span><span class="sxs-lookup"><span data-stu-id="d946c-121">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d946c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d946c-122">See also</span></span>

- [<span data-ttu-id="d946c-123">C # 參考</span><span class="sxs-lookup"><span data-stu-id="d946c-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d946c-124">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d946c-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d946c-125">C # 預處理器指示詞</span><span class="sxs-lookup"><span data-stu-id="d946c-125">C# Preprocessor Directives</span></span>](./index.md)
