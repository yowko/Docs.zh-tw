---
title: 使用者定義函式和變數
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c2ce474dac44de1ac72811ecd3bc294ba57ce40a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570460"
---
# <a name="user-defined-functions-and-variables"></a><span data-ttu-id="217c4-102">使用者定義函式和變數</span><span class="sxs-lookup"><span data-stu-id="217c4-102">User Defined Functions and Variables</span></span>
<span data-ttu-id="217c4-103"><xref:System.Xml.XPath.XPathNavigator> 類別會提供一組可用來與 <xref:System.Xml.XPath.XPathDocument> 資料互動的方法。</span><span class="sxs-lookup"><span data-stu-id="217c4-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods that are used to interact with <xref:System.Xml.XPath.XPathDocument> data.</span></span> <span data-ttu-id="217c4-104">您可以透過實作擴充函式和變數供 XPath 查詢運算式使用，提供標準 XPath 函式。</span><span class="sxs-lookup"><span data-stu-id="217c4-104">You can supplement the standard XPath functions by implementing extension functions and variables for use by XPath query expressions.</span></span> <span data-ttu-id="217c4-105"><xref:System.Xml.XPath.XPathExpression.SetContext%2A> 方法可以接受衍生自 <xref:System.Xml.Xsl.XsltContext> 的使用者定義內容。</span><span class="sxs-lookup"><span data-stu-id="217c4-105">The <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method can accept a user defined context derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="217c4-106">使用者定義函式是由自訂內容解析。</span><span class="sxs-lookup"><span data-stu-id="217c4-106">User defined functions are resolved by the custom context.</span></span>  
  
 <span data-ttu-id="217c4-107">擴充函式和變數在防範 XML 插入式攻擊時可能很有用。</span><span class="sxs-lookup"><span data-stu-id="217c4-107">Extension functions and variables can be useful in prevention of XML injection attacks.</span></span> <span data-ttu-id="217c4-108">在這些案例中，使用者輸入會指派給自訂變數並由擴充函式處理，而非與處理指示串連的原始輸入。</span><span class="sxs-lookup"><span data-stu-id="217c4-108">In these scenarios user input is assigned to custom variables and processed by extension functions, not as raw input concatenated with processing instructions.</span></span> <span data-ttu-id="217c4-109">擴充函式和變數包含使用者輸入，因此它只會依照設計者的預期方式針對 XML 資料運作。</span><span class="sxs-lookup"><span data-stu-id="217c4-109">Extension functions and variables contain user input so that it only acts on XML data as intended by the designer.</span></span>  
  
 <span data-ttu-id="217c4-110">若要使用擴充功能，您必須實作自訂 <xref:System.Xml.Xsl.XsltContext> 類別以及支援擴充函式和變數的 <xref:System.Xml.Xsl.IXsltContextFunction> 和 <xref:System.Xml.Xsl.IXsltContextVariable> 介面。</span><span class="sxs-lookup"><span data-stu-id="217c4-110">To use extensions you implement a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span> <span data-ttu-id="217c4-111"><xref:System.Xml.XPath.XPathExpression> 會將具有其 <xref:System.Xml.Xsl.XsltArgumentList> 的使用者輸入加入至自訂 <xref:System.Xml.Xsl.XsltContext>。</span><span class="sxs-lookup"><span data-stu-id="217c4-111">An <xref:System.Xml.XPath.XPathExpression> adds user input with its <xref:System.Xml.Xsl.XsltArgumentList> to the custom <xref:System.Xml.Xsl.XsltContext>.</span></span>  
  
 <span data-ttu-id="217c4-112"><xref:System.Xml.XPath.XPathExpression> 代表 <xref:System.Xml.XPath.XPathNavigator> 用來尋找和處理運算式所識別之節點的已編譯查詢。</span><span class="sxs-lookup"><span data-stu-id="217c4-112">The <xref:System.Xml.XPath.XPathExpression> represents a compiled query that <xref:System.Xml.XPath.XPathNavigator> uses to find and process the nodes identified by the expression.</span></span>  
  
 <span data-ttu-id="217c4-113">下列範例顯示衍生自 <xref:System.Xml.Xsl.XsltContext> 之自訂內容類別的實作。</span><span class="sxs-lookup"><span data-stu-id="217c4-113">The following example shows implementation of a custom context class derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="217c4-114">程式碼中的註解將描述類別成員以及它們在自訂函式中的用法。</span><span class="sxs-lookup"><span data-stu-id="217c4-114">Comments in the code describe class members and their use in custom functions.</span></span> <span data-ttu-id="217c4-115">函式和變數實作以及使用這些實作的範例應用程式都會遵循這個程式碼區段。</span><span class="sxs-lookup"><span data-stu-id="217c4-115">Function and variable implementations and a sample application that uses these implementations follow this code segment.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 <span data-ttu-id="217c4-116">下列程式碼會實作 <xref:System.Xml.Xsl.IXsltContextFunction>。</span><span class="sxs-lookup"><span data-stu-id="217c4-116">The following code implements <xref:System.Xml.Xsl.IXsltContextFunction>.</span></span> <span data-ttu-id="217c4-117">實作 <xref:System.Xml.Xsl.IXsltContextFunction> 的類別會解析並執行使用者定義函式。</span><span class="sxs-lookup"><span data-stu-id="217c4-117">The class that implements <xref:System.Xml.Xsl.IXsltContextFunction> resolves and executes user-defined functions.</span></span> <span data-ttu-id="217c4-118">此範例會使用下列宣告所識別的函式：`private int CountChar(string title, char charTocount)`。</span><span class="sxs-lookup"><span data-stu-id="217c4-118">This example uses the function identified by the declaration: `private int CountChar(string title, char charTocount)`.</span></span>  
  
 <span data-ttu-id="217c4-119">程式碼註解將描述類別成員。</span><span class="sxs-lookup"><span data-stu-id="217c4-119">Code comments describe class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 <span data-ttu-id="217c4-120">下列程式碼會實作 <xref:System.Xml.Xsl.IXsltContextVariable>。</span><span class="sxs-lookup"><span data-stu-id="217c4-120">The following code implements <xref:System.Xml.Xsl.IXsltContextVariable>.</span></span> <span data-ttu-id="217c4-121">這個類別會在執行階段中解析 XPath 查詢運算式中使用者定義變數的參考。</span><span class="sxs-lookup"><span data-stu-id="217c4-121">This class resolves references to user-defined variables in XPath query expressions at run time.</span></span> <span data-ttu-id="217c4-122">這個類別的執行個體是由自訂 <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> 類別的覆寫 <xref:System.Xml.Xsl.XsltContext> 方法所建立並傳回。</span><span class="sxs-lookup"><span data-stu-id="217c4-122">An instance of this class is created and returned by the overridden <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> method of the custom <xref:System.Xml.Xsl.XsltContext> class.</span></span>  
  
 <span data-ttu-id="217c4-123">程式碼註解將描述類別成員。</span><span class="sxs-lookup"><span data-stu-id="217c4-123">Code comments describe the class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 <span data-ttu-id="217c4-124">如果上述類別定義位於範圍內，下列程式碼就會使用自訂函式來計算 `Tasks.xml` 文件項目中的字元。</span><span class="sxs-lookup"><span data-stu-id="217c4-124">With the previous class definitions in scope, the following code uses the custom function to count characters in the elements of the `Tasks.xml` document.</span></span> <span data-ttu-id="217c4-125">程式碼中的註解將描述編譯自訂函式並針對 `Tasks.xml` 文件執行此函式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="217c4-125">Comments in the code describe the code that compiles the custom function and runs it against the `Tasks.xml` document.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 <span data-ttu-id="217c4-126">此範例會使用下列 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="217c4-126">This example uses the following XML data.</span></span>  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
