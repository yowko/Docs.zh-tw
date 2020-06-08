---
title: 解譯網路追蹤
description: 瞭解如何使用追蹤來捕獲應用程式對 .NET Framework 中的各種 System.Net 類別成員所做的呼叫。
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 7a17e4ba14d8c5fe136667c4eb5bc5b2fd7a8242
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502362"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="2da87-103">解譯網路追蹤</span><span class="sxs-lookup"><span data-stu-id="2da87-103">Interpreting Network Tracing</span></span>
<span data-ttu-id="2da87-104">啟用網路追蹤時，您可以使用追蹤來擷取應用程式對各種 <xref:System.Net> 類別成員的呼叫。</span><span class="sxs-lookup"><span data-stu-id="2da87-104">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="2da87-105">這些呼叫的輸出可能類似下列範例。</span><span class="sxs-lookup"><span data-stu-id="2da87-105">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="2da87-106">在上述範例中，[588] 是目前執行緒的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="2da87-106">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="2da87-107">(4357) 和 (4387) 時間戳記表示自應用程式啟動後所經歷的毫秒數。</span><span class="sxs-lookup"><span data-stu-id="2da87-107">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="2da87-108">時間戳記後面的資料會顯示應用程式進入和結束 **Socket.Send** 方法。</span><span class="sxs-lookup"><span data-stu-id="2da87-108">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="2da87-109">執行 **Send** 方法之物件的唯一識別碼是 33574638。</span><span class="sxs-lookup"><span data-stu-id="2da87-109">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="2da87-110">方法結束追蹤包含傳回值 (上例中為 61)。</span><span class="sxs-lookup"><span data-stu-id="2da87-110">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="2da87-111">網路追蹤可以擷取您的應用程式使用應用程式層級通訊協定，例如超文字傳輸通訊協定 (HTTP)，所傳送或接收的網路流量。</span><span class="sxs-lookup"><span data-stu-id="2da87-111">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="2da87-112">此資料可以擷取成文字或十六進位資料。</span><span class="sxs-lookup"><span data-stu-id="2da87-112">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="2da87-113">當您指定 **includehex** 作為 **tracemode** 屬性的值時，可以使用十六進位資料。</span><span class="sxs-lookup"><span data-stu-id="2da87-113">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="2da87-114">（如需此屬性的詳細資訊，請參閱[如何：設定網路追蹤](how-to-configure-network-tracing.md)。）下列範例追蹤是使用**includehex**產生的。</span><span class="sxs-lookup"><span data-stu-id="2da87-114">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="2da87-115">若要省略十六進位資料，請指定 **protocolonly** 作為 **tracemode** 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="2da87-115">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="2da87-116">當指定 **protocolonly** 時，下列範例會顯示追蹤。</span><span class="sxs-lookup"><span data-stu-id="2da87-116">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="2da87-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2da87-117">See also</span></span>

- [<span data-ttu-id="2da87-118">啟用網路追蹤</span><span class="sxs-lookup"><span data-stu-id="2da87-118">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="2da87-119">如何：設定網路追蹤</span><span class="sxs-lookup"><span data-stu-id="2da87-119">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="2da87-120">以 .NET Framework 進行網路追蹤</span><span class="sxs-lookup"><span data-stu-id="2da87-120">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
