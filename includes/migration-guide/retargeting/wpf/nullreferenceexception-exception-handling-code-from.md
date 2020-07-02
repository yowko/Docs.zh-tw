---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614389"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a><span data-ttu-id="626b3-101">ImageSourceConverter.ConvertFrom 之例外狀況處理程式碼中的 NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="626b3-101">NullReferenceException in exception handling code from ImageSourceConverter.ConvertFrom</span></span>

#### <a name="details"></a><span data-ttu-id="626b3-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="626b3-102">Details</span></span>

<span data-ttu-id="626b3-103"><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> 的例外狀況處理程式碼錯誤已導致擲回不正確的 <xref:System.NullReferenceException?displayProperty=fullName>，而不是預期的例外狀況 (<xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> 或 <xref:System.IO.FileNotFoundException?displayProperty=fullName>)。</span><span class="sxs-lookup"><span data-stu-id="626b3-103">An error in the exception handling code for <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> caused an incorrect <xref:System.NullReferenceException?displayProperty=fullName> to be thrown instead of the intended exception ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> or <xref:System.IO.FileNotFoundException?displayProperty=fullName>).</span></span> <span data-ttu-id="626b3-104">這項變更會修正該錯誤，讓該方法現在擲回正確的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="626b3-104">This change corrects that error so that the method now throws the right exception.</span></span> <p/><span data-ttu-id="626b3-105">根據預設，所有以 .NET Framework 4.6.2 和更早版本為目標的應用程式會繼續擲回 <xref:System.NullReferenceException?displayProperty=fullName> 以提供相容性。</span><span class="sxs-lookup"><span data-stu-id="626b3-105">By default all applications targeting .NET Framework 4.6.2 and earlier continue to throw <xref:System.NullReferenceException?displayProperty=fullName> for compatibility.</span></span> <span data-ttu-id="626b3-106">以 .NET Framework 4.7 和以上版本為目標的開發人員應該會看到正確的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="626b3-106">Developers targeting .NET Framework 4.7 and above should see the right exceptions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="626b3-107">建議</span><span class="sxs-lookup"><span data-stu-id="626b3-107">Suggestion</span></span>

<span data-ttu-id="626b3-108">開發人員若想要在以 .NET Framework 4.7 或更新版本為目標時還原成取得 <xref:System.NullReferenceException?displayProperty=fullName>，可以在其應用程式的 App.config 檔案中新增/合併下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="626b3-108">Developers who wish to revert to getting <xref:System.NullReferenceException?displayProperty=fullName> when targeting .NET Framework 4.7 or later can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="626b3-109">名稱</span><span class="sxs-lookup"><span data-stu-id="626b3-109">Name</span></span>    | <span data-ttu-id="626b3-110">值</span><span class="sxs-lookup"><span data-stu-id="626b3-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="626b3-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="626b3-111">Scope</span></span>   | <span data-ttu-id="626b3-112">Edge</span><span class="sxs-lookup"><span data-stu-id="626b3-112">Edge</span></span>        |
| <span data-ttu-id="626b3-113">版本</span><span class="sxs-lookup"><span data-stu-id="626b3-113">Version</span></span> | <span data-ttu-id="626b3-114">4.7</span><span class="sxs-lookup"><span data-stu-id="626b3-114">4.7</span></span>         |
| <span data-ttu-id="626b3-115">類型</span><span class="sxs-lookup"><span data-stu-id="626b3-115">Type</span></span>    | <span data-ttu-id="626b3-116">正在重定目標</span><span class="sxs-lookup"><span data-stu-id="626b3-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="626b3-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="626b3-117">Affected APIs</span></span>

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
