---
title: 重大變更： UTF-7 程式碼路徑已淘汰
description: 瞭解 UTF7 和 UTF7Encoding 的函式已淘汰的核心 .NET 程式庫中的 .NET 5.0 重大變更。
ms.date: 11/01/2020
ms.openlocfilehash: d58305f59a30cdf31a525c3789bd6497201c50ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760465"
---
# <a name="utf-7-code-paths-are-obsolete"></a><span data-ttu-id="548f8-103">UTF-7 程式碼路徑已淘汰</span><span class="sxs-lookup"><span data-stu-id="548f8-103">UTF-7 code paths are obsolete</span></span>

<span data-ttu-id="548f8-104">UTF-7 編碼不再廣泛使用於應用程式，而許多規格現在禁止在交換中 [使用](https://security.stackexchange.com/a/68609/3573) 。</span><span class="sxs-lookup"><span data-stu-id="548f8-104">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="548f8-105">有時也會在不預期遇到 UTF-7 編碼資料的應用程式中， [用來做為攻擊向量](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) 。</span><span class="sxs-lookup"><span data-stu-id="548f8-105">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="548f8-106">Microsoft 會警告您使用， <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> 因為它不會提供錯誤偵測。</span><span class="sxs-lookup"><span data-stu-id="548f8-106">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="548f8-107">因此， <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 屬性和函式 <xref:System.Text.UTF7Encoding.%23ctor%2A> 現在已過時。</span><span class="sxs-lookup"><span data-stu-id="548f8-107">Consequently, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are now obsolete.</span></span> <span data-ttu-id="548f8-108">此外， <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 也 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> 不再允許您指定 `UTF-7` 。</span><span class="sxs-lookup"><span data-stu-id="548f8-108">Additionally, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> and <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> no longer allow you to specify `UTF-7`.</span></span>

## <a name="change-description"></a><span data-ttu-id="548f8-109">變更描述</span><span class="sxs-lookup"><span data-stu-id="548f8-109">Change description</span></span>

<span data-ttu-id="548f8-110">先前，您可以使用 api 建立 UTF-7 編碼的實例 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="548f8-110">Previously, you could create an instance of the UTF-7 encoding by using the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span></span> <span data-ttu-id="548f8-111">例如：</span><span class="sxs-lookup"><span data-stu-id="548f8-111">For example:</span></span>

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

<span data-ttu-id="548f8-112">此外，方法會列舉表示 UTF-7 編碼的實例 <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> ，此方法會列舉 <xref:System.Text.Encoding> 系統上已註冊的所有實例。</span><span class="sxs-lookup"><span data-stu-id="548f8-112">Additionally, an instance that represents the UTF-7 encoding was enumerated by the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method, which enumerates all the <xref:System.Text.Encoding> instances registered on the system.</span></span>

<span data-ttu-id="548f8-113">從 .NET 5.0 開始， <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 屬性和函式 <xref:System.Text.UTF7Encoding.%23ctor%2A> 已淘汰，並產生警告 `SYSLIB0001` (或 `MSLIB0001` 預覽版本) 。</span><span class="sxs-lookup"><span data-stu-id="548f8-113">Starting in .NET 5.0, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are obsolete and produce warning `SYSLIB0001` (or `MSLIB0001` in preview versions).</span></span> <span data-ttu-id="548f8-114">不過，若要減少呼叫端在使用類別時所收到的警告數目 <xref:System.Text.UTF7Encoding> ， <xref:System.Text.UTF7Encoding> 類型本身不會標示為過時。</span><span class="sxs-lookup"><span data-stu-id="548f8-114">However, to reduce the number of warnings that callers receive when using the <xref:System.Text.UTF7Encoding> class, the <xref:System.Text.UTF7Encoding> type itself is not marked obsolete.</span></span>

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

<span data-ttu-id="548f8-115">此外， <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 方法會將編碼名稱 `utf-7` 和字碼頁視為 `65000` `unknown` 。</span><span class="sxs-lookup"><span data-stu-id="548f8-115">Additionally, the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> methods treat the encoding name `utf-7` and the code page `65000` as `unknown`.</span></span> <span data-ttu-id="548f8-116">將編碼視為 `unknown` 會導致方法擲回 <xref:System.ArgumentException> 。</span><span class="sxs-lookup"><span data-stu-id="548f8-116">Treating the encoding as `unknown` causes the method to throw an <xref:System.ArgumentException>.</span></span>

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

<span data-ttu-id="548f8-117">最後， <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> 方法不會在它所傳回的陣列中包含 utf-7 編碼 <xref:System.Text.EncodingInfo> 。</span><span class="sxs-lookup"><span data-stu-id="548f8-117">Finally, the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method doesn't include the UTF-7 encoding in the <xref:System.Text.EncodingInfo> array that it returns.</span></span> <span data-ttu-id="548f8-118">因為無法具現化，所以會排除編碼。</span><span class="sxs-lookup"><span data-stu-id="548f8-118">The encoding is excluded because it cannot be instantiated.</span></span>

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

## <a name="reason-for-change"></a><span data-ttu-id="548f8-119">變更的原因</span><span class="sxs-lookup"><span data-stu-id="548f8-119">Reason for change</span></span>

<span data-ttu-id="548f8-120">許多應用程式 `Encoding.GetEncoding("encoding-name")` 都使用不受信任的來源所提供的編碼名稱值來呼叫。</span><span class="sxs-lookup"><span data-stu-id="548f8-120">Many applications call `Encoding.GetEncoding("encoding-name")` with an encoding name value that's provided by an untrusted source.</span></span> <span data-ttu-id="548f8-121">例如，網頁用戶端或伺服器可能會採用 `charset` 標頭的部分 `Content-Type` ，並直接將值傳遞給 `Encoding.GetEncoding` 而不需要驗證。</span><span class="sxs-lookup"><span data-stu-id="548f8-121">For example, a web client or server might take the `charset` portion of the `Content-Type` header and pass the value directly to `Encoding.GetEncoding` without validating it.</span></span> <span data-ttu-id="548f8-122">這可能會讓惡意端點指定 `Content-Type: ...; charset=utf-7` ，這可能會導致接收應用程式行為失常。</span><span class="sxs-lookup"><span data-stu-id="548f8-122">This could allow a malicious endpoint to specify `Content-Type: ...; charset=utf-7`, which could cause the receiving application to misbehave.</span></span>

<span data-ttu-id="548f8-123">此外，停用 UTF-7 程式碼路徑可讓編譯器優化，例如 Blazor 所使用的編譯器，以完全從產生的應用程式中移除這些程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="548f8-123">Additionally, disabling UTF-7 code paths allows optimizing compilers, such as those used by Blazor, to remove these code paths entirely from the resulting application.</span></span> <span data-ttu-id="548f8-124">如此一來，經過編譯的應用程式就能以更有效率的方式執行，並減少磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="548f8-124">As a result, the compiled applications run more efficiently and take less disk space.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="548f8-125">引進的版本</span><span class="sxs-lookup"><span data-stu-id="548f8-125">Version introduced</span></span>

<span data-ttu-id="548f8-126">5.0</span><span class="sxs-lookup"><span data-stu-id="548f8-126">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="548f8-127">建議的動作</span><span class="sxs-lookup"><span data-stu-id="548f8-127">Recommended action</span></span>

<span data-ttu-id="548f8-128">在大多數情況下，您不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="548f8-128">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="548f8-129">不過，對於先前已啟用與 UTF-7 相關的程式碼路徑的應用程式，請考慮下列指導方針。</span><span class="sxs-lookup"><span data-stu-id="548f8-129">However, for apps that have previously activated UTF-7-related code paths, consider the guidance that follows.</span></span>

- <span data-ttu-id="548f8-130">如果您的應用程式 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 使用不受信任的來源所提供的未知編碼名稱來呼叫：</span><span class="sxs-lookup"><span data-stu-id="548f8-130">If your app calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> with unknown encoding names provided by an untrusted source:</span></span>

  <span data-ttu-id="548f8-131">相反地，請將編碼名稱與可設定的允許清單進行比較。</span><span class="sxs-lookup"><span data-stu-id="548f8-131">Instead, compare the encoding names against a configurable allow list.</span></span> <span data-ttu-id="548f8-132">可設定的允許清單至少應包含產業標準 "utf-8"。</span><span class="sxs-lookup"><span data-stu-id="548f8-132">The configurable allow list should at minimum include the industry-standard "utf-8".</span></span> <span data-ttu-id="548f8-133">視您的用戶端和法規需求而定，您可能也需要允許特定區域的編碼方式，例如「GB18030」。</span><span class="sxs-lookup"><span data-stu-id="548f8-133">Depending on your clients and regulatory requirements, you may also need to allow region-specific encodings, such as "GB18030".</span></span>

  <span data-ttu-id="548f8-134">如果您未執行允許清單， <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 將會傳回 <xref:System.Text.Encoding> 系統內建或透過自訂註冊的任何 <xref:System.Text.EncodingProvider> 。</span><span class="sxs-lookup"><span data-stu-id="548f8-134">If you don't implement an allow list, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> will return any <xref:System.Text.Encoding> that's built into the system or that's registered via a custom <xref:System.Text.EncodingProvider>.</span></span> <span data-ttu-id="548f8-135">請審核您服務的需求，以驗證這是所需的行為。</span><span class="sxs-lookup"><span data-stu-id="548f8-135">Audit your service's requirements to validate that this is the desired behavior.</span></span> <span data-ttu-id="548f8-136">除非您的應用程式重新啟用本文稍後所述的相容性參數，否則會繼續預設為停用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="548f8-136">UTF-7 continues to be disabled by default unless your application re-enables the compatibility switch mentioned later in this article.</span></span>

- <span data-ttu-id="548f8-137">如果您使用 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 的是或 <xref:System.Text.UTF7Encoding> 在自己的通訊協定或檔案格式內：</span><span class="sxs-lookup"><span data-stu-id="548f8-137">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="548f8-138">切換為使用 <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> 或 <xref:System.Text.UTF8Encoding> 。</span><span class="sxs-lookup"><span data-stu-id="548f8-138">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="548f8-139">UTF-8 是業界標準，可廣泛地跨語言、作業系統和執行時間支援。</span><span class="sxs-lookup"><span data-stu-id="548f8-139">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="548f8-140">使用 UTF-8 可簡化未來的程式碼維護，讓它能夠與其余的生態系統更互通。</span><span class="sxs-lookup"><span data-stu-id="548f8-140">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="548f8-141">如果您要比較 <xref:System.Text.Encoding> 實例與 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="548f8-141">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="548f8-142">相反地，請考慮針對已知的 UTF-7 字碼頁執行檢查，也就是 `65000` 。</span><span class="sxs-lookup"><span data-stu-id="548f8-142">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="548f8-143">藉由與字碼頁比較，您可以避免出現警告，也會處理一些邊緣案例，例如，如果有人呼叫 `new UTF7Encoding()` 或子類別化型別。</span><span class="sxs-lookup"><span data-stu-id="548f8-143">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

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

- <span data-ttu-id="548f8-144">如果您必須使用 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 或 <xref:System.Text.UTF7Encoding> ：</span><span class="sxs-lookup"><span data-stu-id="548f8-144">If you must use <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding>:</span></span>

  <span data-ttu-id="548f8-145">您可以隱藏 `SYSLIB0001` 程式碼或專案 *.csproj* 檔案內的警告。</span><span class="sxs-lookup"><span data-stu-id="548f8-145">You can suppress the `SYSLIB0001` warning in code or within your project's *.csproj* file.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  > [!NOTE]
  > <span data-ttu-id="548f8-146">隱藏 `SYSLIB0001` 只會停用 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 和 <xref:System.Text.UTF7Encoding> obsoletion 警告。</span><span class="sxs-lookup"><span data-stu-id="548f8-146">Suppressing `SYSLIB0001` only disables the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> and <xref:System.Text.UTF7Encoding> obsoletion warnings.</span></span> <span data-ttu-id="548f8-147">它不會停用任何其他警告，也不會變更 Api 的行為 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="548f8-147">It doesn't disable any other warnings or change the behavior of APIs like <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="548f8-148">如果您必須支援 `Encoding.GetEncoding("utf-7", ...)` ：</span><span class="sxs-lookup"><span data-stu-id="548f8-148">If you must support `Encoding.GetEncoding("utf-7", ...)`:</span></span>

  <span data-ttu-id="548f8-149">您可以透過相容性參數重新啟用此功能的支援。</span><span class="sxs-lookup"><span data-stu-id="548f8-149">You can re-enable support for this via a compatibility switch.</span></span> <span data-ttu-id="548f8-150">此相容性參數可以在應用程式的 *.csproj* 檔案或 [執行時間設定檔](../../../run-time-config/index.md)中指定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="548f8-150">This compatibility switch can be specified in the application's *.csproj* file or in a [run-time configuration file](../../../run-time-config/index.md), as shown in the following examples.</span></span>

  <span data-ttu-id="548f8-151">在應用程式的 *.csproj* 檔案中：</span><span class="sxs-lookup"><span data-stu-id="548f8-151">In the application's *.csproj* file:</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="548f8-152">在應用程式的 *runtimeconfig.template.json* file：</span><span class="sxs-lookup"><span data-stu-id="548f8-152">In the application's *runtimeconfig.template.json* file:</span></span>

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > <span data-ttu-id="548f8-153">如果您重新啟用對 UTF-7 的支援，您應該對呼叫的程式碼執行安全性檢查 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="548f8-153">If you re-enable support for UTF-7, you should perform a security review of code that calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="548f8-154">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="548f8-154">Affected APIs</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- Security

### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
