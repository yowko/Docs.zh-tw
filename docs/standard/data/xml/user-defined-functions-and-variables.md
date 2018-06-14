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
# <a name="user-defined-functions-and-variables"></a>使用者定義函式和變數
<xref:System.Xml.XPath.XPathNavigator> 類別會提供一組可用來與 <xref:System.Xml.XPath.XPathDocument> 資料互動的方法。 您可以透過實作擴充函式和變數供 XPath 查詢運算式使用，提供標準 XPath 函式。 <xref:System.Xml.XPath.XPathExpression.SetContext%2A> 方法可以接受衍生自 <xref:System.Xml.Xsl.XsltContext> 的使用者定義內容。 使用者定義函式是由自訂內容解析。  
  
 擴充函式和變數在防範 XML 插入式攻擊時可能很有用。 在這些案例中，使用者輸入會指派給自訂變數並由擴充函式處理，而非與處理指示串連的原始輸入。 擴充函式和變數包含使用者輸入，因此它只會依照設計者的預期方式針對 XML 資料運作。  
  
 若要使用擴充功能，您必須實作自訂 <xref:System.Xml.Xsl.XsltContext> 類別以及支援擴充函式和變數的 <xref:System.Xml.Xsl.IXsltContextFunction> 和 <xref:System.Xml.Xsl.IXsltContextVariable> 介面。 <xref:System.Xml.XPath.XPathExpression> 會將具有其 <xref:System.Xml.Xsl.XsltArgumentList> 的使用者輸入加入至自訂 <xref:System.Xml.Xsl.XsltContext>。  
  
 <xref:System.Xml.XPath.XPathExpression> 代表 <xref:System.Xml.XPath.XPathNavigator> 用來尋找和處理運算式所識別之節點的已編譯查詢。  
  
 下列範例顯示衍生自 <xref:System.Xml.Xsl.XsltContext> 之自訂內容類別的實作。 程式碼中的註解將描述類別成員以及它們在自訂函式中的用法。 函式和變數實作以及使用這些實作的範例應用程式都會遵循這個程式碼區段。  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 下列程式碼會實作 <xref:System.Xml.Xsl.IXsltContextFunction>。 實作 <xref:System.Xml.Xsl.IXsltContextFunction> 的類別會解析並執行使用者定義函式。 此範例會使用下列宣告所識別的函式：`private int CountChar(string title, char charTocount)`。  
  
 程式碼註解將描述類別成員。  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 下列程式碼會實作 <xref:System.Xml.Xsl.IXsltContextVariable>。 這個類別會在執行階段中解析 XPath 查詢運算式中使用者定義變數的參考。 這個類別的執行個體是由自訂 <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> 類別的覆寫 <xref:System.Xml.Xsl.XsltContext> 方法所建立並傳回。  
  
 程式碼註解將描述類別成員。  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 如果上述類別定義位於範圍內，下列程式碼就會使用自訂函式來計算 `Tasks.xml` 文件項目中的字元。 程式碼中的註解將描述編譯自訂函式並針對 `Tasks.xml` 文件執行此函式的程式碼。  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 此範例會使用下列 XML 資料。  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
