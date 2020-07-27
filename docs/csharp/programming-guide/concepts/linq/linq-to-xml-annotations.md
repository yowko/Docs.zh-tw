---
title: LINQ to XML 註釋
description: 瞭解如何使用 LINQ to XML 中的注釋，將任何任意類型的任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: e7da666139c10b26de37816693202d96498f52d8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165573"
---
# <a name="linq-to-xml-annotations"></a><span data-ttu-id="11359-103">LINQ to XML 註釋</span><span class="sxs-lookup"><span data-stu-id="11359-103">LINQ to XML Annotations</span></span>

<span data-ttu-id="11359-104">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的註釋可讓您將任意型別的任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="11359-104">Annotations in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="11359-105">若要將附註加入到 XML 元件 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>) 中，您可以呼叫 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="11359-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="11359-106">您可以按照型別擷取附註。</span><span class="sxs-lookup"><span data-stu-id="11359-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="11359-107">請注意，這些附註不是 XML 資訊集的一部分；它們無法進行序列化或還原序列化。</span><span class="sxs-lookup"><span data-stu-id="11359-107">Note that annotations are not part of the XML infoset; they are not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="11359-108">方法</span><span class="sxs-lookup"><span data-stu-id="11359-108">Methods</span></span>

<span data-ttu-id="11359-109">使用附註時，您可以使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="11359-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="11359-110">方法</span><span class="sxs-lookup"><span data-stu-id="11359-110">Method</span></span>|<span data-ttu-id="11359-111">描述</span><span class="sxs-lookup"><span data-stu-id="11359-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="11359-112">將物件加入到 <xref:System.Xml.Linq.XObject> 的附註清單。</span><span class="sxs-lookup"><span data-stu-id="11359-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="11359-113">從 <xref:System.Xml.Linq.XObject> 取得指定之型別的第一個附註物件。</span><span class="sxs-lookup"><span data-stu-id="11359-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="11359-114">針對 <xref:System.Xml.Linq.XObject> 取得指定之型別的附註集合。</span><span class="sxs-lookup"><span data-stu-id="11359-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="11359-115">從 <xref:System.Xml.Linq.XObject> 移除指定之型別的附註。</span><span class="sxs-lookup"><span data-stu-id="11359-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
