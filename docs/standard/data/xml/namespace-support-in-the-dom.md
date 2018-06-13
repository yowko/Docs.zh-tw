---
title: DOM 中支援的命名空間
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e91ce2b36462780925dcaef701583a966c5f59b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569447"
---
# <a name="namespace-support-in-the-dom"></a><span data-ttu-id="d8b0c-102">DOM 中支援的命名空間</span><span class="sxs-lookup"><span data-stu-id="d8b0c-102">Namespace Support in the DOM</span></span>
<span data-ttu-id="d8b0c-103">XML 文件物件模型 (DOM) 具有完全的命名空間感知。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-103">The XML Document Object Model (DOM) is completely namespace-aware.</span></span> <span data-ttu-id="d8b0c-104">只有命名空間感知 XML 文件受支援。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-104">Only namespace-aware XML documents are supported.</span></span> <span data-ttu-id="d8b0c-105">全球資訊網協會 (W3C) 指定實作層級 1 的 DOM 應用程式可不具備命名空間感知，而 DOM 層級 2 功能則具有命名空間感知。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-105">The World Wide Web Consortium (W3C) specifies that DOM applications that implement Level 1 can be non-namespace-aware, and DOM Level 2 features are namespace-aware.</span></span> <span data-ttu-id="d8b0c-106">然而，不論方法是來自層級 1 或層級 2 DOM 建議事項，XML DOM 中所有的功能都具有命名空間感知。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-106">However, all features in the XML DOM are namespace-aware, regardless if the method is from the Level 1 or Level 2 DOM Recommendation.</span></span>  
  
 <span data-ttu-id="d8b0c-107">例如，若在非命名空間設定中呼叫 `setAttribute("A:b", "123")` (根據 DOM 層級 1 建議事項中所指定)，並不會產生具有前置詞 `A` 和區域名稱 `b` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-107">For example, in a non-namespace-aware setting, calling `setAttribute("A:b", "123")`, as specified in the DOM Level 1 Recommendation, does not result in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="d8b0c-108">它會產生具有值 `A:b` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-108">It would result in an attribute with the value `A:b`.</span></span>  
  
 <span data-ttu-id="d8b0c-109">若在具有命名空間感知的環境中呼叫 DOM 層級 2 `setAttribute("A:b", "123")`，則會產生具有前置詞 `A` 和區域名稱 `b` 的屬性。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-109">In a namespace-aware environment, the call to the DOM Level 2 `setAttribute("A:b", "123")` results in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="d8b0c-110">這就是 Microsoft .NET Framework DOM 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-110">This is how the Microsoft .NET Framework DOM works.</span></span>  
  
 <span data-ttu-id="d8b0c-111">因此，對於所有採用名稱參數的方法，這些方法也會採用前置詞來限定名稱。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-111">Therefore, for all methods that take a name parameter, these methods also take a prefix to qualify the name.</span></span> <span data-ttu-id="d8b0c-112">名稱參數 (例如 **setAttribute** DOM 層級 1 方法中的 `A:b`) 會以下列方式剖析：</span><span class="sxs-lookup"><span data-stu-id="d8b0c-112">The name parameter, such as the `A:b` in the **setAttribute** DOM Level 1 method, is parsed as follows:</span></span>  
  
-   <span data-ttu-id="d8b0c-113">如果沒有冒號 (:) 字元，則區域名稱會設為 `name` 參數，而前置詞和 NamespaceURI 則為空字串。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-113">If there are no colon (:) characters, then the local name is set to the `name` parameter, and the prefix and NamespaceURI are empty strings.</span></span>  
  
-   <span data-ttu-id="d8b0c-114">如果找到冒號，則名稱會根據第一個冒號字元的位置分成兩個部分。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-114">If a colon is found, then the name is split into two parts based on the position of the first colon character.</span></span> <span data-ttu-id="d8b0c-115">前置詞會設為冒號之前找到的字串，而且區域名稱會設為冒號之後找到的字串。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-115">The prefix is set to the string found before the colon, and local name is set to the string found after the colon.</span></span> <span data-ttu-id="d8b0c-116">對於沒有採用 NamespaceURI 值的方法，NamespaceURI 不會解析且會維持設定為空字串。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-116">For methods that do not take a NamespaceURI value, the NamespaceURI is not resolved and remains set to empty string.</span></span> <span data-ttu-id="d8b0c-117">否則，NamespaceURI 會設為傳入方法的字串。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-117">Otherwise, the NamespaceURI is set to the string passed to the method.</span></span> <span data-ttu-id="d8b0c-118">如果沒有指定前置詞，那麼 **Save** 方法以及 **InnerXml** 和 **OuterXml** 屬性會失敗。</span><span class="sxs-lookup"><span data-stu-id="d8b0c-118">If the prefix is undefined, then the **Save** method and **InnerXml** and **OuterXml** properties fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b0c-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="d8b0c-119">See Also</span></span>  
 [<span data-ttu-id="d8b0c-120">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="d8b0c-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
