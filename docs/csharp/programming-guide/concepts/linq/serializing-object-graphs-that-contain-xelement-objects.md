---
title: "序列化包含 XElement 物件的物件圖形 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: fcbc3951-3cc4-4d0f-9259-e97549ed68f0
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 752092f7455fa0a10efcaa41166b66ff1f87b16e
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-object-graphs-that-contain-xelement-objects-c"></a>序列化包含 XElement 物件的物件圖形 (C#)
本主題介紹如何序列化包含 <xref:System.Xml.Linq.XElement> 類型之物件參考的物件圖形。 為了簡化這類型的序列化，<xref:System.Xml.Linq.XElement> 會實作 <xref:System.Xml.Serialization.IXmlSerializable> 介面。  
  
 請注意，只有 <xref:System.Xml.Linq.XElement> 類別才會實作序列化。  
  
## <a name="in-this-section"></a>本章節內容  
  
|主題|說明|  
|-----------|-----------------|  
|[如何：使用 XmlSerializer 進行序列化 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-xmlserializer.md)|示範如何使用 <xref:System.Xml.Serialization.XmlSerializer> 進行序列化。|  
|[如何：使用 DataContractSerializer 進行序列化 (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-serialize-using-datacontractserializer.md)|示範如何使用 <xref:System.Runtime.Serialization.DataContractSerializer> 進行序列化。|  
  
## <a name="see-also"></a>另請參閱  
 [進階 LINQ to XML 程式設計 (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
