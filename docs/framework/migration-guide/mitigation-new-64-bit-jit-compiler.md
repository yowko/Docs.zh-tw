---
title: 風險降低：新的 64 位元 JIT 編譯器
description: 瞭解 .NET Framework 4.6 中包含的新64位 JIT 編譯程式，以及編譯期間可能發生的非預期行為或例外狀況。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compiler, 64-bit
- JIT compilation, 64-bit
- RyuJIT compiler
ms.assetid: 0332dabc-72c5-4bdc-8975-20d717802b17
ms.openlocfilehash: 228c286f6c5620dc838df5002edc60863a0fe4e2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256595"
---
# <a name="mitigation-new-64-bit-jit-compiler"></a><span data-ttu-id="58e6f-103">風險降低：新的 64 位元 JIT 編譯器</span><span class="sxs-lookup"><span data-stu-id="58e6f-103">Mitigation: New 64-bit JIT Compiler</span></span>

<span data-ttu-id="58e6f-104">從 .NET Framework 4.6 開始，執行時間包含新的64位 JIT 編譯程式，可進行即時編譯。</span><span class="sxs-lookup"><span data-stu-id="58e6f-104">Starting with .NET Framework 4.6, the runtime includes a new 64-bit JIT compiler for just-in-time compilation.</span></span> <span data-ttu-id="58e6f-105">此變更不會影響使用32位 JIT 編譯程式的編譯。</span><span class="sxs-lookup"><span data-stu-id="58e6f-105">This change does not affect compilation with the 32-bit JIT compiler.</span></span>  
  
## <a name="unexpected-behavior-or-exceptions"></a><span data-ttu-id="58e6f-106">未預期的行為或例外狀況</span><span class="sxs-lookup"><span data-stu-id="58e6f-106">Unexpected behavior or exceptions</span></span>  

 <span data-ttu-id="58e6f-107">在某些情況下，使用新版 64 位元 JIT 編譯器的編譯會產生執行階段例外狀況，或是產生在執行舊版 64 位元 JIT 編譯器所編譯的程式碼時未觀察到的行為。</span><span class="sxs-lookup"><span data-stu-id="58e6f-107">In some cases, compilation with the new 64-bit JIT compiler results in a runtime exception or in behavior that is not observed when executing code compiled by the older 64-bit JIT compiler.</span></span> <span data-ttu-id="58e6f-108">下列是已知的差異︰</span><span class="sxs-lookup"><span data-stu-id="58e6f-108">The known differences include the following:</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="58e6f-109">上述所有已知問題都已在隨 .NET Framework 4.6.2 發行的新版 64 位元編譯器中解決。</span><span class="sxs-lookup"><span data-stu-id="58e6f-109">All of these known issues have been addressed in the new 64-bit compiler released with the .NET Framework 4.6.2.</span></span> <span data-ttu-id="58e6f-110">大部分問題已在隨附於 Windows Update 的 .NET Framework 4.6 和 4.6.1 服務版本中解決。</span><span class="sxs-lookup"><span data-stu-id="58e6f-110">Most have also been addressed in service releases of the .NET Framework 4.6 and 4.6.1 that are included with Windows Update.</span></span> <span data-ttu-id="58e6f-111">將您的 Windows 版本更新至最新版或升級至 .NET Framework 4.6.2，即可解決這些問題。</span><span class="sxs-lookup"><span data-stu-id="58e6f-111">You can eliminate these issues by ensuring that your version of Windows is up to date, or by upgrading to the .NET Framework 4.6.2.</span></span>  
  
- <span data-ttu-id="58e6f-112">在某些情況下，已開啟最佳化的發行組建中的 Unboxing 作業可能會擲回 <xref:System.NullReferenceException>。</span><span class="sxs-lookup"><span data-stu-id="58e6f-112">Under certain conditions, an unboxing operation may throw a <xref:System.NullReferenceException> in Release builds with optimization turned on.</span></span>  
  
- <span data-ttu-id="58e6f-113">在某些情況下，執行大型方法主體中的實際執行程式碼可能會擲回 <xref:System.StackOverflowException>。</span><span class="sxs-lookup"><span data-stu-id="58e6f-113">In some cases, execution of production code in a large method body may throw a <xref:System.StackOverflowException>.</span></span>  
  
- <span data-ttu-id="58e6f-114">某些狀況下，發行組建中傳遞至方法的結構會被視為參考型別而非實值型別。</span><span class="sxs-lookup"><span data-stu-id="58e6f-114">Under certain conditions, structures passed to a method are treated as reference types rather than value types in Release builds.</span></span> <span data-ttu-id="58e6f-115">這個問題的其中一種表現，就是集合中的個別項目會以非預期的順序出現。</span><span class="sxs-lookup"><span data-stu-id="58e6f-115">One of the manifestations of this issue is that the individual items in a collection appear in an unexpected order.</span></span>  
  
- <span data-ttu-id="58e6f-116">在某些情況下，如果啟用最佳化，<xref:System.UInt16> 的值在設定高位元時的比較會不正確。</span><span class="sxs-lookup"><span data-stu-id="58e6f-116">Under certain conditions, the comparison of <xref:System.UInt16> values with their high bit set is incorrect if optimization is enabled.</span></span>  
  
- <span data-ttu-id="58e6f-117">在某些情況下，尤其是初始化陣列值時，使用 <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL 指令初始化記憶體，可能會以不正確的值初始化記憶體。</span><span class="sxs-lookup"><span data-stu-id="58e6f-117">Under certain conditions, particularly when initializing array values, memory initialization by the <xref:System.Reflection.Emit.OpCodes.Initblk?displayProperty=nameWithType> IL instruction may initialize memory with an incorrect value.</span></span> <span data-ttu-id="58e6f-118">這會造成未處理的例外狀況或不正確的輸出。</span><span class="sxs-lookup"><span data-stu-id="58e6f-118">This can result either in an unhandled exception or incorrect output.</span></span>  
  
- <span data-ttu-id="58e6f-119">在少數情況下，如果啟用編譯器最佳化，條件式位元測試可能會傳回不正確的 <xref:System.Boolean> 值或擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="58e6f-119">Under certain rare conditions, a conditional bit test can return the incorrect <xref:System.Boolean> value or throw an exception if compiler optimizations are enabled.</span></span>  
  
- <span data-ttu-id="58e6f-120">某些狀況下，如果使用 `if` 陳述式在進入 `try` 區塊之前和自 `try` 區塊退出時測試某項條件，而且也在 `catch` 或 `finally` 區塊中評估該條件時，新版 64 位元 JIT 編譯器在最佳化程式碼時會將 `if` 條件自 `catch` 或 `finally` 區塊中移除。</span><span class="sxs-lookup"><span data-stu-id="58e6f-120">Under certain conditions, if an `if` statement is used to test for a condition before entering  a `try` block and in the exit from the `try` block, and the same condition is evaluated in the `catch` or `finally` block, the new 64-bit JIT compiler removes the `if` condition from the `catch` or `finally` block when it optimizes code.</span></span> <span data-ttu-id="58e6f-121">因此，`catch` 或 `finally` 區塊的 `if` 陳述式中的程式碼會無條件執行。</span><span class="sxs-lookup"><span data-stu-id="58e6f-121">As a result, code inside the `if` statement in the `catch` or `finally` block is executed unconditionally.</span></span>  
  
<a name="General"></a>

## <a name="mitigation-of-known-issues"></a><span data-ttu-id="58e6f-122">降低已知問題的風險</span><span class="sxs-lookup"><span data-stu-id="58e6f-122">Mitigation of known issues</span></span>  

 <span data-ttu-id="58e6f-123">如果您遇到上述問題，可以採取以下任一種方式來解決︰</span><span class="sxs-lookup"><span data-stu-id="58e6f-123">If you encounter the issues listed above, you can address them by doing any of the following:</span></span>  
  
- <span data-ttu-id="58e6f-124">升級至 .NET Framework 4.6.2。</span><span class="sxs-lookup"><span data-stu-id="58e6f-124">Upgrade to the .NET Framework 4.6.2.</span></span> <span data-ttu-id="58e6f-125">隨附於 .NET Framework 4.6.2 中的新版 64 位元編譯器可以解決這些已知問題。</span><span class="sxs-lookup"><span data-stu-id="58e6f-125">The new 64-bit compiler included with the .NET Framework 4.6.2 addresses each of these known issues.</span></span>  
  
- <span data-ttu-id="58e6f-126">執行 Windows Update，確定您的 Windows 已更新至最新版本。</span><span class="sxs-lookup"><span data-stu-id="58e6f-126">Ensure that your version of Windows is up to date by running Windows Update.</span></span> <span data-ttu-id="58e6f-127">.NET Framework 4.6 和 4.6.1 的服務更新可解決上述問題中除了 Unboxing 作業之 <xref:System.NullReferenceException> 以外的所有問題。</span><span class="sxs-lookup"><span data-stu-id="58e6f-127">Service updates to the .NET Framework 4.6 and 4.6.1 address each of these issues except the <xref:System.NullReferenceException> in an unboxing operation.</span></span>  
  
- <span data-ttu-id="58e6f-128">使用舊版 64 位元 JIT 編譯器編譯。</span><span class="sxs-lookup"><span data-stu-id="58e6f-128">Compile with the older 64-bit JIT compiler.</span></span> <span data-ttu-id="58e6f-129">如需如何進行的詳細資訊，請參閱[降低其他問題的風險](#Other)一節。</span><span class="sxs-lookup"><span data-stu-id="58e6f-129">See the [Mitigation of other issues](#Other) section for more information on how to do this.</span></span>  
  
<a name="Other"></a>

## <a name="mitigation-of-other-issues"></a><span data-ttu-id="58e6f-130">降低其他問題的風險</span><span class="sxs-lookup"><span data-stu-id="58e6f-130">Mitigation of other issues</span></span>  

 <span data-ttu-id="58e6f-131">如果舊版和新版 64 位元 JIT 編譯器編譯的程式碼之間有任何差異，或是使用新版 64 位元 JIT 編譯器編譯的應用程式偵錯版本和發行版本之間有任何差異，您可以使用舊版 64 位元 JIT 編譯器搭配下列方式來編譯應用程式：</span><span class="sxs-lookup"><span data-stu-id="58e6f-131">If you encounter any other difference in behavior between code compiled with the older 64-bit compiler and the new 64-bit JIT compiler, or between the debug and release versions of your app that are both compiled with the new 64-bit JIT compiler, you can do the following to compile your app with the older 64-bit JIT compiler:</span></span>  
  
- <span data-ttu-id="58e6f-132">針對每個應用程式，您可以將專案加入 [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) 至應用程式的設定檔。</span><span class="sxs-lookup"><span data-stu-id="58e6f-132">On a per-application basis, you can add the [\<useLegacyJit>](../configure-apps/file-schema/runtime/uselegacyjit-element.md) element to your application's configuration file.</span></span> <span data-ttu-id="58e6f-133">下列程式碼會停止以新版 64 位元 JIT 編譯器進行編譯，改用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="58e6f-133">The following disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>  
        <runtime>  
           <useLegacyJit enabled="1" />  
        </runtime>  
    </configuration>  
    ```  
  
- <span data-ttu-id="58e6f-134">若以每一使用者為基礎，您可以將名為 `useLegacyJit` 的 `REG_DWORD` 值加入至登錄的 `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="58e6f-134">On a per-user basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="58e6f-135">值為 1 會啟用舊版 64 位元 JIT 編譯器；值為 0 會停用它，並啟用新版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="58e6f-135">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
- <span data-ttu-id="58e6f-136">若以每一電腦為基礎，您可以將名為 `useLegacyJit` 的 `REG_DWORD` 值加入至登錄的 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="58e6f-136">On a per-machine basis, you can add a `REG_DWORD` value named `useLegacyJit` to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key of the registry.</span></span> <span data-ttu-id="58e6f-137">值為 1 會啟用舊版 64 位元 JIT 編譯器；值為 0 會停用它，並啟用新版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="58e6f-137">A value of 1 enables the legacy 64-bit JIT compiler; a value of 0 disables it and enables the new 64-bit JIT compiler.</span></span>  
  
 <span data-ttu-id="58e6f-138">您也可以前往 [Microsoft Connect](https://connect.microsoft.com/VisualStudio) 回報錯誤，讓我們知道問題所在。</span><span class="sxs-lookup"><span data-stu-id="58e6f-138">You can also let us know about the problem by reporting a bug on [Microsoft Connect](https://connect.microsoft.com/VisualStudio).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e6f-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58e6f-139">See also</span></span>

- [<span data-ttu-id="58e6f-140">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="58e6f-140">Application compatibility</span></span>](application-compatibility.md)
- [<span data-ttu-id="58e6f-141">\<useLegacyJit> 元素</span><span class="sxs-lookup"><span data-stu-id="58e6f-141">\<useLegacyJit> Element</span></span>](../configure-apps/file-schema/runtime/uselegacyjit-element.md)
