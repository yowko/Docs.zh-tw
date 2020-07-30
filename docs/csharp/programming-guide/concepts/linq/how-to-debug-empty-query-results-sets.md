---
title: '如何調試空的查詢結果集（c #）'
description: 瞭解如何對空的查詢結果集進行調試。 如果開發人員撰寫了查詢，如同 XML 不在命名空間中，則可能會發生這些設定。
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: ad6d39697e5a59fe23ca700ceeb2a9860d05bb94
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302902"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="d8b05-104">如何調試空的查詢結果集（c #）</span><span class="sxs-lookup"><span data-stu-id="d8b05-104">How to debug empty query results sets (C#)</span></span>
<span data-ttu-id="d8b05-105">查詢 XML 時所遇到的其中一個最常見的問題是，如果 XML 樹狀結構有預設的命名空間，即使 XML 不在命名空間中，開發人員有時候還是會撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="d8b05-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="d8b05-106">本主題中的第一組範例會顯示將 XML 載入預設命名空間而且查詢錯誤的常見方式。</span><span class="sxs-lookup"><span data-stu-id="d8b05-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="d8b05-107">第二組範例顯示所需的修正，讓您可以在命名空間中查詢 XML。</span><span class="sxs-lookup"><span data-stu-id="d8b05-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="d8b05-108">如需詳細資訊，請參閱[命名空間概觀 (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="d8b05-108">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8b05-109">範例</span><span class="sxs-lookup"><span data-stu-id="d8b05-109">Example</span></span>  
 <span data-ttu-id="d8b05-110">此範例顯示 XML 在命名空間中的建立，以及傳回空結果集的查詢。</span><span class="sxs-lookup"><span data-stu-id="d8b05-110">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="d8b05-111">此範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="d8b05-111">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="d8b05-112">範例</span><span class="sxs-lookup"><span data-stu-id="d8b05-112">Example</span></span>  
 <span data-ttu-id="d8b05-113">此範例顯示 XML 在命名空間中的建立，以及編碼正確的查詢。</span><span class="sxs-lookup"><span data-stu-id="d8b05-113">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="d8b05-114">解決方案是要宣告與初始化 <xref:System.Xml.Linq.XNamespace> 物件，並在指定 <xref:System.Xml.Linq.XName> 物件時使用。</span><span class="sxs-lookup"><span data-stu-id="d8b05-114">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="d8b05-115">在這個情況下，<xref:System.Xml.Linq.XContainer.Elements%2A> 方法的引數為 <xref:System.Xml.Linq.XName> 物件。</span><span class="sxs-lookup"><span data-stu-id="d8b05-115">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 <span data-ttu-id="d8b05-116">此範例會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="d8b05-116">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
