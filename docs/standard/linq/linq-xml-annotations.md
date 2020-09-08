---
title: 批註-LINQ to XML
description: 瞭解如何使用 LINQ to XML 中的注釋，將任何任意型別的任何任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。
ms.date: 07/20/2015
ms.assetid: 54e7b9d0-07f5-488f-9065-b6e6b870f810
ms.openlocfilehash: 80710b3596fc37ed76f23e31d1d781c64d0bc909
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552240"
---
# <a name="linq-to-xml-annotations-linq-to-xml"></a><span data-ttu-id="0213e-103">LINQ to XML 注釋 (LINQ to XML) </span><span class="sxs-lookup"><span data-stu-id="0213e-103">LINQ to XML annotations (LINQ to XML)</span></span>

<span data-ttu-id="0213e-104">LINQ to XML 中的批註可讓您將任何任意型別的任何任意物件與 XML 樹狀結構中的任何 XML 元件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="0213e-104">Annotations in LINQ to XML enable you to associate any arbitrary object of any arbitrary type with any XML component in an XML tree.</span></span>

<span data-ttu-id="0213e-105">若要將附註加入到 XML 元件 (例如，<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute>) 中，您可以呼叫 <xref:System.Xml.Linq.XObject.AddAnnotation%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="0213e-105">To add an annotation to an XML component, such as an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>, you call the <xref:System.Xml.Linq.XObject.AddAnnotation%2A> method.</span></span> <span data-ttu-id="0213e-106">您可以按照型別擷取附註。</span><span class="sxs-lookup"><span data-stu-id="0213e-106">You retrieve annotations by type.</span></span>

<span data-ttu-id="0213e-107">請注意，批註不是 XML 資訊集的一部分;它們未序列化或還原序列化。</span><span class="sxs-lookup"><span data-stu-id="0213e-107">Note that annotations aren't part of the XML infoset; they're not serialized or deserialized.</span></span>

## <a name="methods"></a><span data-ttu-id="0213e-108">方法</span><span class="sxs-lookup"><span data-stu-id="0213e-108">Methods</span></span>

<span data-ttu-id="0213e-109">使用附註時，您可以使用下列方法：</span><span class="sxs-lookup"><span data-stu-id="0213e-109">You can use the following methods when working with annotations:</span></span>

|<span data-ttu-id="0213e-110">方法</span><span class="sxs-lookup"><span data-stu-id="0213e-110">Method</span></span>|<span data-ttu-id="0213e-111">描述</span><span class="sxs-lookup"><span data-stu-id="0213e-111">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|<span data-ttu-id="0213e-112">將物件加入到 <xref:System.Xml.Linq.XObject> 的附註清單。</span><span class="sxs-lookup"><span data-stu-id="0213e-112">Adds an object to the annotation list of an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotation%2A>|<span data-ttu-id="0213e-113">從 <xref:System.Xml.Linq.XObject> 取得指定之型別的第一個附註物件。</span><span class="sxs-lookup"><span data-stu-id="0213e-113">Gets the first annotation object of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.Annotations%2A>|<span data-ttu-id="0213e-114">針對 <xref:System.Xml.Linq.XObject> 取得指定之型別的附註集合。</span><span class="sxs-lookup"><span data-stu-id="0213e-114">Gets a collection of annotations of the specified type for an <xref:System.Xml.Linq.XObject>.</span></span>|
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|<span data-ttu-id="0213e-115">從 <xref:System.Xml.Linq.XObject> 移除指定之型別的附註。</span><span class="sxs-lookup"><span data-stu-id="0213e-115">Removes the annotations of the specified type from an <xref:System.Xml.Linq.XObject>.</span></span>|
