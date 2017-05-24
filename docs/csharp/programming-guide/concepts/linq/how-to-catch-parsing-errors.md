---
title: "如何：攔截剖析錯誤 (C#) | Microsoft Docs"
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
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bf9469a328d80cca95fc5da2b143a494490089c2
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-catch-parsing-errors-c"></a>如何：攔截剖析錯誤 (C#)
這個主題顯示如何偵測格式錯誤或無效的 XML。  
  
 使用 <xref:System.Xml.XmlReader> 實作 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]。 如果將格式錯誤或無效的 XML 傳遞到 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]，基礎 <xref:System.Xml.XmlReader> 類別會擲出例外狀況。 剖析 XML 的各種方法 (例如 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>) 不會攔截例外狀況。然後，您的應用程式就可以攔截例外狀況。  
  
## <a name="example"></a>範例  
 下列程式碼嘗試剖析無效的 XML：  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 執行此程式碼時，它會擲回例外狀況：  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 如需預期 <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>、<xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> 和 <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> 方法擲回之例外狀況的資訊，請參閱 <xref:System.Xml.XmlReader> 文件。  
  
## <a name="see-also"></a>另請參閱  
 [剖析 XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
