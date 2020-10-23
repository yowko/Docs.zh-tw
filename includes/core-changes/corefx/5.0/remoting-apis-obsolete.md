---
ms.openlocfilehash: 35041a035041fd4ad5402e1bc0dd137a74d4f949
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434942"
---
### <a name="remoting-apis-are-obsolete"></a><span data-ttu-id="0b6e7-101">遠端 Api 已淘汰</span><span class="sxs-lookup"><span data-stu-id="0b6e7-101">Remoting APIs are obsolete</span></span>

<span data-ttu-id="0b6e7-102">某些遠端相關的 Api 會標示為已淘汰，並 `SYSLIB0010` 在編譯時期產生警告。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-102">Some remoting-related APIs are marked as obsolete and generate a `SYSLIB0010` warning at compile time.</span></span> <span data-ttu-id="0b6e7-103">這些 Api 可能會在未來的 .NET 版本中移除。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-103">These APIs may be removed in a future version of .NET.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0b6e7-104">變更描述</span><span class="sxs-lookup"><span data-stu-id="0b6e7-104">Change description</span></span>

<span data-ttu-id="0b6e7-105">下列遠端 Api 已標示為過時。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-105">The following remoting APIs are marked obsolete.</span></span>

| <span data-ttu-id="0b6e7-106">API</span><span class="sxs-lookup"><span data-stu-id="0b6e7-106">API</span></span> | <span data-ttu-id="0b6e7-107">標記為過時</span><span class="sxs-lookup"><span data-stu-id="0b6e7-107">Marked obsolete in...</span></span> |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="0b6e7-108">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="0b6e7-108">5.0 RC1</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="0b6e7-109">5.0 RC1</span><span class="sxs-lookup"><span data-stu-id="0b6e7-109">5.0 RC1</span></span> |

<span data-ttu-id="0b6e7-110">在 .NET Framework 2.x-4.x 中， <xref:System.MarshalByRefObject.GetLifetimeService> 和 <xref:System.MarshalByRefObject.InitializeLifetimeService> 方法會控制與 .net 遠端處理相關之實例的存留期。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-110">In .NET Framework 2.x - 4.x, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods control the lifetime of instances involved with .NET remoting.</span></span> <span data-ttu-id="0b6e7-111">在 .NET Core 2.x-3.x 中，這些方法一律會 <xref:System.PlatformNotSupportedException> 在執行時間擲回。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-111">In .NET Core 2.x- 3.x, these methods always throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

<span data-ttu-id="0b6e7-112">在 .NET 5.0 和更新版本中， <xref:System.MarshalByRefObject.GetLifetimeService> 和 <xref:System.MarshalByRefObject.InitializeLifetimeService> 方法會標示為「已淘汰」為「警告」，但會 <xref:System.PlatformNotSupportedException> 在執行時間繼續擲回。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-112">In .NET 5.0 and later versions, the <xref:System.MarshalByRefObject.GetLifetimeService> and <xref:System.MarshalByRefObject.InitializeLifetimeService> methods are marked obsolete as warning, but continue to throw a <xref:System.PlatformNotSupportedException> at run time.</span></span>

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

<span data-ttu-id="0b6e7-113">這是僅限編譯時期的變更。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-113">This is a compile-time only change.</span></span> <span data-ttu-id="0b6e7-114">舊版 .NET Core 沒有任何執行時間變更。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-114">There is no run-time change from previous versions of .NET Core.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0b6e7-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="0b6e7-115">Reason for change</span></span>

<span data-ttu-id="0b6e7-116">[.Net 遠端處理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) 是一種舊版技術。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-116">[.NET remoting](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) is a legacy technology.</span></span> <span data-ttu-id="0b6e7-117">它可讓您在另一個進程中具現化物件 (可能甚至在不同的電腦上) 並與該物件互動，就像是一般的同進程 .NET 物件實例一樣。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-117">It allows instantiating an object in another process (potentially even on a different machine) and interacting with that object as if it were an ordinary, in-process .NET object instance.</span></span> <span data-ttu-id="0b6e7-118">.NET 遠端基礎結構只存在於 .NET Framework 2.x. x 中。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-118">The .NET remoting infrastructure only exists in .NET Framework 2.x - 4.x.</span></span> <span data-ttu-id="0b6e7-119">.NET Core 和 .NET 5.0 和更新版本不支援 .NET 遠端處理，而遠端 Api 不存在或一律在這些執行時間擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-119">.NET Core and .NET 5.0 and later versions don't have support for .NET remoting, and the remoting APIs either don't exist or always throw exceptions on these runtimes.</span></span>

<span data-ttu-id="0b6e7-120">為了協助開發人員遠離這些 Api，我們會 obsoleting 選取的遠端處理相關 Api。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-120">To help steer developers away from these APIs, we are obsoleting selected remoting-related APIs.</span></span> <span data-ttu-id="0b6e7-121">這些 Api 可能會在未來的 .NET 版本中完全移除。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-121">These APIs may be removed entirely in a future version of .NET.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0b6e7-122">引進的版本</span><span class="sxs-lookup"><span data-stu-id="0b6e7-122">Version introduced</span></span>

<span data-ttu-id="0b6e7-123">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="0b6e7-123">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0b6e7-124">建議的動作</span><span class="sxs-lookup"><span data-stu-id="0b6e7-124">Recommended action</span></span>

- <span data-ttu-id="0b6e7-125">請考慮使用以 WCF 或 HTTP 為基礎的 REST 服務，與其他應用程式或電腦之間的物件進行通訊。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-125">Consider using WCF or HTTP-based REST services to communicate with objects in other applications or across machines.</span></span> <span data-ttu-id="0b6e7-126">如需詳細資訊，請參閱 [.NET FRAMEWORK .Net Core 上無法使用的技術](../../../../docs/core/porting/net-framework-tech-unavailable.md)。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-126">For more information, see [.NET Framework technologies unavailable on .NET Core](../../../../docs/core/porting/net-framework-tech-unavailable.md).</span></span>

- <span data-ttu-id="0b6e7-127">如果您必須繼續使用已淘汰的 Api，您可以在程式 `SYSLIB0010` 代碼中隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-127">If you must continue to use the obsolete APIs, you can suppress the `SYSLIB0010` warning in code.</span></span>

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  <span data-ttu-id="0b6e7-128">您也可以隱藏專案檔中的警告，這會針對專案中的所有原始程式檔停用警告。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-128">You can also suppress the warning in your project file, which disables the warning for all source files in the project.</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="0b6e7-129">隱藏 `SYSLIB0010` 只會停用遠端 API obsoletion 警告。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-129">Suppressing `SYSLIB0010` disables only the remoting API obsoletion warnings.</span></span> <span data-ttu-id="0b6e7-130">它不會停用任何其他警告。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-130">It does not disable any other warnings.</span></span> <span data-ttu-id="0b6e7-131">此外，它也不會變更永遠擲回的硬式編碼執行時間行為 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="0b6e7-131">Additionally, it doesn't change the hardcoded run-time behavior of always throwing <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="category"></a><span data-ttu-id="0b6e7-132">類別</span><span class="sxs-lookup"><span data-stu-id="0b6e7-132">Category</span></span>

<span data-ttu-id="0b6e7-133">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="0b6e7-133">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0b6e7-134">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="0b6e7-134">Affected APIs</span></span>

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
