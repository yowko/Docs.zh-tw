---
ms.openlocfilehash: 1cb6e953aa57c72ee6a2665c521bada10e0786cf
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455780"
---
### <a name="utf-7-code-paths-are-obsolete"></a><span data-ttu-id="64d62-101">UTF-7 程式碼路徑已過時</span><span class="sxs-lookup"><span data-stu-id="64d62-101">UTF-7 code paths are obsolete</span></span>

<span data-ttu-id="64d62-102">在應用程式之間已不再使用 UTF-7 編碼，而許多規格現在[禁止其](https://security.stackexchange.com/a/68609/3573)在交換中使用。</span><span class="sxs-lookup"><span data-stu-id="64d62-102">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="64d62-103">它偶爾也會[用來做為](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7)應用程式中的攻擊向量，而不預期會遇到以 utf-7 編碼的資料。</span><span class="sxs-lookup"><span data-stu-id="64d62-103">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="64d62-104">Microsoft 會警告您使用， <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> 因為它不會提供錯誤偵測。</span><span class="sxs-lookup"><span data-stu-id="64d62-104">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="64d62-105">因此， <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 屬性和構造函式 <xref:System.Text.UTF7Encoding.%23ctor%2A> 現在已過時。</span><span class="sxs-lookup"><span data-stu-id="64d62-105">Consequently, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are now obsolete.</span></span> <span data-ttu-id="64d62-106">此外， <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 和不再 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> 允許您指定 `UTF-7` 。</span><span class="sxs-lookup"><span data-stu-id="64d62-106">Additionally, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> and <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> no longer allow you to specify `UTF-7`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="64d62-107">變更描述</span><span class="sxs-lookup"><span data-stu-id="64d62-107">Change description</span></span>

<span data-ttu-id="64d62-108">之前，您可以使用 api 來建立 UTF-7 編碼的實例 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="64d62-108">Previously, you could create an instance of the UTF-7 encoding by using the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span></span> <span data-ttu-id="64d62-109">例如：</span><span class="sxs-lookup"><span data-stu-id="64d62-109">For example:</span></span>

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

<span data-ttu-id="64d62-110">此外，表示 UTF-7 編碼的實例是由方法所列舉 <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> ，這會列舉 <xref:System.Text.Encoding> 系統上註冊的所有實例。</span><span class="sxs-lookup"><span data-stu-id="64d62-110">Additionally, an instance that represents the UTF-7 encoding was enumerated by the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method, which enumerates all the <xref:System.Text.Encoding> instances registered on the system.</span></span>

<span data-ttu-id="64d62-111">從 .NET 5.0 開始， <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 屬性和構造函式 <xref:System.Text.UTF7Encoding.%23ctor%2A> 已過時， `SYSLIB0001` (或 `MSLIB0001` 預覽版本) 中產生警告。</span><span class="sxs-lookup"><span data-stu-id="64d62-111">Starting in .NET 5.0, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are obsolete and produce warning `SYSLIB0001` (or `MSLIB0001` in preview versions).</span></span> <span data-ttu-id="64d62-112">不過，若要減少呼叫端在使用類別時所收到的警告數目 <xref:System.Text.UTF7Encoding> ， <xref:System.Text.UTF7Encoding> 類型本身不會標示為已過時。</span><span class="sxs-lookup"><span data-stu-id="64d62-112">However, to reduce the number of warnings that callers receive when using the <xref:System.Text.UTF7Encoding> class, the <xref:System.Text.UTF7Encoding> type itself is not marked obsolete.</span></span>

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

<span data-ttu-id="64d62-113">此外，方法會將 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 編碼名稱 `utf-7` 和字碼頁視為 `65000` `unknown` 。</span><span class="sxs-lookup"><span data-stu-id="64d62-113">Additionally, the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> methods treat the encoding name `utf-7` and the code page `65000` as `unknown`.</span></span> <span data-ttu-id="64d62-114">將編碼方式視為 `unknown` 會導致方法擲回 <xref:System.ArgumentException> 。</span><span class="sxs-lookup"><span data-stu-id="64d62-114">Treating the encoding as `unknown` causes the method to throw an <xref:System.ArgumentException>.</span></span>

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

<span data-ttu-id="64d62-115">最後， <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> 方法不會在它所傳回的陣列中包含 utf-7 編碼 <xref:System.Text.EncodingInfo> 。</span><span class="sxs-lookup"><span data-stu-id="64d62-115">Finally, the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method doesn't include the UTF-7 encoding in the <xref:System.Text.EncodingInfo> array that it returns.</span></span> <span data-ttu-id="64d62-116">已排除編碼，因為它無法具現化。</span><span class="sxs-lookup"><span data-stu-id="64d62-116">The encoding is excluded because it cannot be instantiated.</span></span>

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

#### <a name="reason-for-change"></a><span data-ttu-id="64d62-117">變更的原因</span><span class="sxs-lookup"><span data-stu-id="64d62-117">Reason for change</span></span>

<span data-ttu-id="64d62-118">許多應用程式 `Encoding.GetEncoding("encoding-name")` 會使用不受信任來源所提供的編碼名稱值來呼叫。</span><span class="sxs-lookup"><span data-stu-id="64d62-118">Many applications call `Encoding.GetEncoding("encoding-name")` with an encoding name value that's provided by an untrusted source.</span></span> <span data-ttu-id="64d62-119">例如，web 用戶端或伺服器可能會取得 `charset` 標頭的部分 `Content-Type` ，並直接將值傳遞給， `Encoding.GetEncoding` 而不進行驗證。</span><span class="sxs-lookup"><span data-stu-id="64d62-119">For example, a web client or server might take the `charset` portion of the `Content-Type` header and pass the value directly to `Encoding.GetEncoding` without validating it.</span></span> <span data-ttu-id="64d62-120">這可能會讓惡意端點指定 `Content-Type: ...; charset=utf-7` ，這可能會導致接收應用程式行為失常。</span><span class="sxs-lookup"><span data-stu-id="64d62-120">This could allow a malicious endpoint to specify `Content-Type: ...; charset=utf-7`, which could cause the receiving application to misbehave.</span></span>

<span data-ttu-id="64d62-121">此外，停用 UTF-7 程式碼路徑，可以優化編譯器（例如 Blazor 所使用的編譯器），以從產生的應用程式中完全移除這些程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="64d62-121">Additionally, disabling UTF-7 code paths allows optimizing compilers, such as those used by Blazor, to remove these code paths entirely from the resulting application.</span></span> <span data-ttu-id="64d62-122">因此，已編譯的應用程式執行效率較高，而且佔用的磁碟空間較少。</span><span class="sxs-lookup"><span data-stu-id="64d62-122">As a result, the compiled applications run more efficiently and take less disk space.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="64d62-123">引進的版本</span><span class="sxs-lookup"><span data-stu-id="64d62-123">Version introduced</span></span>

<span data-ttu-id="64d62-124">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="64d62-124">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="64d62-125">建議的動作</span><span class="sxs-lookup"><span data-stu-id="64d62-125">Recommended action</span></span>

<span data-ttu-id="64d62-126">在大部分的情況下，您不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="64d62-126">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="64d62-127">不過，如果應用程式先前已啟用與 UTF-7 相關的程式碼路徑，請考慮下列指引。</span><span class="sxs-lookup"><span data-stu-id="64d62-127">However, for apps that have previously activated UTF-7-related code paths, consider the guidance that follows.</span></span>

- <span data-ttu-id="64d62-128">如果您的應用程式 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 使用不受信任的來源所提供的未知編碼名稱進行呼叫：</span><span class="sxs-lookup"><span data-stu-id="64d62-128">If your app calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> with unknown encoding names provided by an untrusted source:</span></span>

  <span data-ttu-id="64d62-129">相反地，請將編碼名稱與可設定的允許清單進行比較。</span><span class="sxs-lookup"><span data-stu-id="64d62-129">Instead, compare the encoding names against a configurable allow list.</span></span> <span data-ttu-id="64d62-130">可設定的允許清單至少須包含業界標準的 "utf-8"。</span><span class="sxs-lookup"><span data-stu-id="64d62-130">The configurable allow list should at minimum include the industry-standard "utf-8".</span></span> <span data-ttu-id="64d62-131">視您的用戶端和法規需求而定，您可能也需要允許特定區域的編碼，例如「GB18030」。</span><span class="sxs-lookup"><span data-stu-id="64d62-131">Depending on your clients and regulatory requirements, you may also need to allow region-specific encodings, such as "GB18030".</span></span>

  <span data-ttu-id="64d62-132">如果您未執行允許清單， <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 將會傳回系統內建的任何， <xref:System.Text.Encoding> 或透過自訂註冊的 <xref:System.Text.EncodingProvider> 。</span><span class="sxs-lookup"><span data-stu-id="64d62-132">If you don't implement an allow list, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> will return any <xref:System.Text.Encoding> that's built into the system or that's registered via a custom <xref:System.Text.EncodingProvider>.</span></span> <span data-ttu-id="64d62-133">請審核您的服務需求，以驗證這是否為所需的行為。</span><span class="sxs-lookup"><span data-stu-id="64d62-133">Audit your service's requirements to validate that this is the desired behavior.</span></span> <span data-ttu-id="64d62-134">除非您的應用程式重新啟用本文章稍後所述的相容性參數，否則，預設會繼續停用 UTF-7。</span><span class="sxs-lookup"><span data-stu-id="64d62-134">UTF-7 continues to be disabled by default unless your application re-enables the compatibility switch mentioned later in this article.</span></span>

- <span data-ttu-id="64d62-135">如果您在 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 自己的 <xref:System.Text.UTF7Encoding> 通訊協定或檔案格式中使用或：</span><span class="sxs-lookup"><span data-stu-id="64d62-135">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="64d62-136">切換至使用 <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> 或 <xref:System.Text.UTF8Encoding> 。</span><span class="sxs-lookup"><span data-stu-id="64d62-136">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="64d62-137">UTF-8 是一種業界標準，在語言、作業系統和執行時間之間廣泛支援。</span><span class="sxs-lookup"><span data-stu-id="64d62-137">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="64d62-138">使用 UTF-8 可簡化程式碼的未來維護，使其更能與生態系統的其餘部分互通。</span><span class="sxs-lookup"><span data-stu-id="64d62-138">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="64d62-139">如果您要比較 <xref:System.Text.Encoding> 實例與 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ：</span><span class="sxs-lookup"><span data-stu-id="64d62-139">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="64d62-140">相反地，請考慮對已知的 UTF-7 字碼頁執行檢查，也就是 `65000` 。</span><span class="sxs-lookup"><span data-stu-id="64d62-140">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="64d62-141">藉由比較字碼頁，您可以避免警告，也會處理一些邊緣案例，例如，如果有人呼叫 `new UTF7Encoding()` 或子類別化型別。</span><span class="sxs-lookup"><span data-stu-id="64d62-141">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

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

- <span data-ttu-id="64d62-142">如果您必須使用 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 或 <xref:System.Text.UTF7Encoding> ：</span><span class="sxs-lookup"><span data-stu-id="64d62-142">If you must use <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding>:</span></span>

  <span data-ttu-id="64d62-143">您可以 `SYSLIB0001` 在程式碼或專案的 *.csproj*檔案中隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="64d62-143">You can suppress the `SYSLIB0001` warning in code or within your project's *.csproj* file.</span></span>

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
  > <span data-ttu-id="64d62-144">隱藏 `SYSLIB0001` 只會停用 <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> 和 <xref:System.Text.UTF7Encoding> obsoletion 警告。</span><span class="sxs-lookup"><span data-stu-id="64d62-144">Suppressing `SYSLIB0001` only disables the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> and <xref:System.Text.UTF7Encoding> obsoletion warnings.</span></span> <span data-ttu-id="64d62-145">它不會停用任何其他警告，也不會變更 Api 的行為，例如 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="64d62-145">It doesn't disable any other warnings or change the behavior of APIs like <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="64d62-146">如果您必須支援 `Encoding.GetEncoding("utf-7", ...)` ：</span><span class="sxs-lookup"><span data-stu-id="64d62-146">If you must support `Encoding.GetEncoding("utf-7", ...)`:</span></span>

  <span data-ttu-id="64d62-147">您可以透過相容性參數重新啟用此功能的支援。</span><span class="sxs-lookup"><span data-stu-id="64d62-147">You can re-enable support for this via a compatibility switch.</span></span> <span data-ttu-id="64d62-148">此相容性參數可以在應用程式的 *.csproj*檔案或[執行時間設定檔](../../../../docs/core/run-time-config/index.md)中指定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="64d62-148">This compatibility switch can be specified in the application's *.csproj* file or in a [run-time configuration file](../../../../docs/core/run-time-config/index.md), as shown in the following examples.</span></span>

  <span data-ttu-id="64d62-149">在應用程式的 *.csproj*檔案中：</span><span class="sxs-lookup"><span data-stu-id="64d62-149">In the application's *.csproj* file:</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="64d62-150">在應用程式的*runtimeconfig.template.json* file：</span><span class="sxs-lookup"><span data-stu-id="64d62-150">In the application's *runtimeconfig.template.json* file:</span></span>

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > <span data-ttu-id="64d62-151">如果您重新啟用 UTF-7 的支援，您應該執行呼叫之程式碼的安全性審查 <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="64d62-151">If you re-enable support for UTF-7, you should perform a security review of code that calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="64d62-152">類別</span><span class="sxs-lookup"><span data-stu-id="64d62-152">Category</span></span>

- <span data-ttu-id="64d62-153">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="64d62-153">Core .NET libraries</span></span>
- <span data-ttu-id="64d62-154">安全性</span><span class="sxs-lookup"><span data-stu-id="64d62-154">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="64d62-155">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="64d62-155">Affected APIs</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
