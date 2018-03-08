---
title: "如何：從 URL 擷取通訊協定和通訊埠編號"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 62931273acd41768d131c08510e14ff187d64296
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a><span data-ttu-id="efee2-102">如何：從 URL 擷取通訊協定和通訊埠編號</span><span class="sxs-lookup"><span data-stu-id="efee2-102">How to: Extract a Protocol and Port Number from a URL</span></span>
<span data-ttu-id="efee2-103">下列範例會從 URL 擷取通訊協定和連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="efee2-103">The following example extracts a protocol and port number from a URL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efee2-104">範例</span><span class="sxs-lookup"><span data-stu-id="efee2-104">Example</span></span>  
 <span data-ttu-id="efee2-105">此範例會使用 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> 方法來傳回通訊協定和連接埠號碼 (中間以冒號隔開)。</span><span class="sxs-lookup"><span data-stu-id="efee2-105">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method to return the protocol followed by a colon followed by the port number.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 <span data-ttu-id="efee2-106">規則運算式模式 `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` 的解譯方式如下表所示。</span><span class="sxs-lookup"><span data-stu-id="efee2-106">The regular expression pattern `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` can be interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="efee2-107">模式</span><span class="sxs-lookup"><span data-stu-id="efee2-107">Pattern</span></span>|<span data-ttu-id="efee2-108">描述</span><span class="sxs-lookup"><span data-stu-id="efee2-108">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="efee2-109">在字串開頭開始比對。</span><span class="sxs-lookup"><span data-stu-id="efee2-109">Begin the match at the start of the string.</span></span>|  
|`(?<proto>\w+)`|<span data-ttu-id="efee2-110">比對一個或多個文字字元。</span><span class="sxs-lookup"><span data-stu-id="efee2-110">Match one or more word characters.</span></span> <span data-ttu-id="efee2-111">將這個群組命名為 `proto`。</span><span class="sxs-lookup"><span data-stu-id="efee2-111">Name this group `proto`.</span></span>|  
|`://`|<span data-ttu-id="efee2-112">比對冒號加兩個斜線符號。</span><span class="sxs-lookup"><span data-stu-id="efee2-112">Match a colon followed by two slash marks.</span></span>|  
|`[^/]+?`|<span data-ttu-id="efee2-113">比對一個或多個 (但越少越好) 出現的任何字元，但不包括斜線符號。</span><span class="sxs-lookup"><span data-stu-id="efee2-113">Match one or more occurrences (but as few as possible) of any character other than a slash mark.</span></span>|  
|`(?<port>:\d+)?`|<span data-ttu-id="efee2-114">比對零個或一個出現的冒號外加一個或多個數字字元。</span><span class="sxs-lookup"><span data-stu-id="efee2-114">Match zero or one occurrence of a colon followed by one or more digit characters.</span></span> <span data-ttu-id="efee2-115">將這個群組命名為 `port`。</span><span class="sxs-lookup"><span data-stu-id="efee2-115">Name this group `port`.</span></span>|  
|`/`|<span data-ttu-id="efee2-116">比對斜線符號。</span><span class="sxs-lookup"><span data-stu-id="efee2-116">Match a slash mark.</span></span>|  
  
 <span data-ttu-id="efee2-117"><xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> 方法會展開 `${proto}${port}` 取代序列，以將規則運算式模式中所擷取之兩個具名群組的值串連在一起。</span><span class="sxs-lookup"><span data-stu-id="efee2-117">The <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method expands the `${proto}${port}` replacement sequence, which concatenates the value of the two named groups captured in the regular expression pattern.</span></span> <span data-ttu-id="efee2-118">另一種方便的作法是將 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> 屬性所傳回之集合物件中擷取的字串明確地串連在一起。</span><span class="sxs-lookup"><span data-stu-id="efee2-118">It is a convenient alternative to explicitly concatenating the strings retrieved from the collection object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="efee2-119">此範例會使用 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> 方法搭配兩個替代項目 `${proto}` 和 `${port}`，以便在輸出字串中包含擷取的群組。</span><span class="sxs-lookup"><span data-stu-id="efee2-119">The example uses the <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> method with two substitutions, `${proto}` and `${port}`, to include the captured groups in the output string.</span></span> <span data-ttu-id="efee2-120">您可以改為從相符項目的 <xref:System.Text.RegularExpressions.GroupCollection> 物件中擷取該群組，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="efee2-120">You can retrieve the captured groups from the match's <xref:System.Text.RegularExpressions.GroupCollection> object instead, as the following code shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="efee2-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="efee2-121">See Also</span></span>  
 [<span data-ttu-id="efee2-122">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="efee2-122">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
