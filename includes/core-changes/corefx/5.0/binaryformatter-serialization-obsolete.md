---
ms.openlocfilehash: c5204e8c80cb737338b053c39083c0cc43786447
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517320"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a><span data-ttu-id="27512-101">ASP.NET 應用程式中的 BinaryFormatter 序列化方法已過時且禁止</span><span class="sxs-lookup"><span data-stu-id="27512-101">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>

<span data-ttu-id="27512-102">`Serialize`、和上的和 `Deserialize` 方法 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatter> <xref:System.Runtime.Serialization.IFormatter> 現在已過時。</span><span class="sxs-lookup"><span data-stu-id="27512-102">`Serialize` and `Deserialize` methods on <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter>, and <xref:System.Runtime.Serialization.IFormatter> are now obsolete.</span></span> <span data-ttu-id="27512-103">此外， <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ASP.NET 應用程式預設會禁止序列化。</span><span class="sxs-lookup"><span data-stu-id="27512-103">Additionally, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is prohibited by default for ASP.NET apps.</span></span>

#### <a name="change-description"></a><span data-ttu-id="27512-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="27512-104">Change description</span></span>

<span data-ttu-id="27512-105">由於中的[安全性弱點](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ，下列方法現在已過時。</span><span class="sxs-lookup"><span data-stu-id="27512-105">Due to [security vulnerabilities](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following methods are now obsolete.</span></span> <span data-ttu-id="27512-106">此外，在 ASP.NET 5.0 和更新版本的應用程式中， <xref:System.NotSupportedException> 除非 web 應用程式已重新啟用功能，否則它們會擲回 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 。</span><span class="sxs-lookup"><span data-stu-id="27512-106">Additionally, in ASP.NET 5.0 and later apps, they will throw a <xref:System.NotSupportedException>, unless the web app has re-enabled <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> functionality.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

<span data-ttu-id="27512-107">在 .NET 生態系統中，這些方法會被標示為過時，做為停止使用的一部分 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 。</span><span class="sxs-lookup"><span data-stu-id="27512-107">These methods are marked obsolete as part of an effort to wind down usage of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> within the .NET ecosystem.</span></span>

<span data-ttu-id="27512-108">下列序列化方法現在也已經過時，但沒有任何行為變更：</span><span class="sxs-lookup"><span data-stu-id="27512-108">The following serialization methods are also now obsolete, but have no behavioral changes:</span></span>

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a><span data-ttu-id="27512-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="27512-109">Version introduced</span></span>

<span data-ttu-id="27512-110">5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="27512-110">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="27512-111">建議的動作</span><span class="sxs-lookup"><span data-stu-id="27512-111">Recommended action</span></span>

- <span data-ttu-id="27512-112">停止 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 在您的程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="27512-112">Stop using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in your code.</span></span> <span data-ttu-id="27512-113">相反地，請考慮使用 <xref:System.Text.Json.JsonSerializer> 或 <xref:System.Xml.Serialization.XmlSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="27512-113">Instead, consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="27512-114">如需詳細資訊，請參閱[BinaryFormatter 安全性指南](../../../../docs/standard/serialization/binaryformatter-security-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="27512-114">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

- <span data-ttu-id="27512-115">您可以暫時隱藏 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 編譯時期警告，也就是 `SYSLIB0011` 。</span><span class="sxs-lookup"><span data-stu-id="27512-115">You can temporarily suppress the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> compile-time warning, which is `SYSLIB0011`.</span></span> <span data-ttu-id="27512-116">我們建議您在選擇此選項之前，先徹底評估您的程式碼是否有風險。</span><span class="sxs-lookup"><span data-stu-id="27512-116">We recommend that you thoroughly assess your code for risks before choosing this option.</span></span> <span data-ttu-id="27512-117">抑制警告最簡單的方式，就是使用指示詞來括住個別的呼叫位置 `#pragma` 。</span><span class="sxs-lookup"><span data-stu-id="27512-117">The easiest way to suppress the warnings is to surround the individual call site with `#pragma` directives.</span></span>

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  <span data-ttu-id="27512-118">您也可以在專案檔中隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="27512-118">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  <span data-ttu-id="27512-119">如果您在專案檔中隱藏警告，則會針對專案中的所有程式碼檔案隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="27512-119">If you suppress the warning in the project file, the warning is suppressed for all code files in the project.</span></span> <span data-ttu-id="27512-120">隱藏 SYSLIB0011 並不會隱藏使用其他已淘汰的 Api 所造成的警告。</span><span class="sxs-lookup"><span data-stu-id="27512-120">Suppressing SYSLIB0011 does not suppress warnings caused by using other obsolete APIs.</span></span>

- <span data-ttu-id="27512-121">若要繼續 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 在 ASP.NET apps 中使用，您可以在專案檔中重新啟用它。</span><span class="sxs-lookup"><span data-stu-id="27512-121">To continue using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in ASP.NET apps, you can re-enable it in the project file.</span></span> <span data-ttu-id="27512-122">不過，強烈建議不要這麼做。</span><span class="sxs-lookup"><span data-stu-id="27512-122">However, it's strongly recommended not to do this.</span></span> <span data-ttu-id="27512-123">如需詳細資訊，請參閱[BinaryFormatter 安全性指南](../../../../docs/standard/serialization/binaryformatter-security-guide.md)。</span><span class="sxs-lookup"><span data-stu-id="27512-123">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

<span data-ttu-id="27512-124">如需建議動作的詳細資訊，請參閱[解決 BinaryFormatter obsoletion 和停用錯誤](https://aka.ms/binaryformatter)。</span><span class="sxs-lookup"><span data-stu-id="27512-124">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](https://aka.ms/binaryformatter).</span></span>

#### <a name="category"></a><span data-ttu-id="27512-125">類別</span><span class="sxs-lookup"><span data-stu-id="27512-125">Category</span></span>

- <span data-ttu-id="27512-126">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="27512-126">Core .NET libraries</span></span>
- <span data-ttu-id="27512-127">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="27512-127">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="27512-128">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="27512-128">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
