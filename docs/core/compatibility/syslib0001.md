---
title: SYSLIB0001 警告
description: 瞭解產生編譯時期警告 SYSLIB0001 的 obsoletions。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 58c16879b7d91598ea0848bb0ba95f8fa0200cfe
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333248"
---
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a><span data-ttu-id="b3d83-103">SYSLIB0001：不安全的 UTF-7 編碼</span><span class="sxs-lookup"><span data-stu-id="b3d83-103">SYSLIB0001: The UTF-7 encoding is insecure</span></span>

<span data-ttu-id="b3d83-104">UTF-7 編碼不再廣泛使用於應用程式，而許多規格現在禁止在交換中 [使用](https://security.stackexchange.com/a/68609/3573) 。</span><span class="sxs-lookup"><span data-stu-id="b3d83-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="b3d83-105">有時也會在不預期遇到 UTF-7 編碼資料的應用程式中， [用來做為攻擊向量](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) 。</span><span class="sxs-lookup"><span data-stu-id="b3d83-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="b3d83-106">Microsoft 會警告您使用， <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> 因為它不會提供錯誤偵測。</span><span class="sxs-lookup"><span data-stu-id="b3d83-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="b3d83-107">因此，下列 Api 會標示為已淘汰，從 .NET 5.0 開始。</span><span class="sxs-lookup"><span data-stu-id="b3d83-107">Consequently, the following APIs are marked obsolete, starting in .NET 5.0.</span></span> <span data-ttu-id="b3d83-108">使用這些 Api `SYSLIB0001` 時，會在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="b3d83-108">Use of these APIs generates warning `SYSLIB0001` at compile time.</span></span>

- <span data-ttu-id="b3d83-109"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 屬性</span><span class="sxs-lookup"><span data-stu-id="b3d83-109"><xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property</span></span>
- <span data-ttu-id="b3d83-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> 構造 函數</span><span class="sxs-lookup"><span data-stu-id="b3d83-110"><xref:System.Text.UTF7Encoding.%23ctor%2A> constructors</span></span>

## <a name="workarounds"></a><span data-ttu-id="b3d83-111">因應措施</span><span class="sxs-lookup"><span data-stu-id="b3d83-111">Workarounds</span></span>

- <span data-ttu-id="b3d83-112">如果您使用 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 的是或 <xref:System.Text.UTF7Encoding> 在自己的通訊協定或檔案格式內：</span><span class="sxs-lookup"><span data-stu-id="b3d83-112">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="b3d83-113">切換為使用 <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> 或 <xref:System.Text.UTF8Encoding> 。</span><span class="sxs-lookup"><span data-stu-id="b3d83-113">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="b3d83-114">UTF-8 是業界標準，可廣泛地跨語言、作業系統和執行時間支援。</span><span class="sxs-lookup"><span data-stu-id="b3d83-114">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="b3d83-115">使用 UTF-8 可簡化未來的程式碼維護，讓它能夠與其余的生態系統更互通。</span><span class="sxs-lookup"><span data-stu-id="b3d83-115">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="b3d83-116">如果您要比較 <xref:System.Text.Encoding> 實例與 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="b3d83-116">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="b3d83-117">相反地，請考慮針對已知的 UTF-7 字碼頁執行檢查，也就是 `65000` 。</span><span class="sxs-lookup"><span data-stu-id="b3d83-117">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="b3d83-118">藉由與字碼頁比較，您可以避免出現警告，也會處理一些邊緣案例，例如，如果有人呼叫 `new UTF7Encoding()` 或子類別化型別。</span><span class="sxs-lookup"><span data-stu-id="b3d83-118">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

## <a name="see-also"></a><span data-ttu-id="b3d83-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3d83-119">See also</span></span>

- [<span data-ttu-id="b3d83-120">UTF-7 程式碼路徑已淘汰</span><span class="sxs-lookup"><span data-stu-id="b3d83-120">UTF-7 code paths are obsolete</span></span>](3.1-5.0.md#utf-7-code-paths-are-obsolete)
