---
title: HOW TO：剖析字串 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: b97ce93c1018ec48649ab8b259d5f1a07109b9fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956369"
---
# <a name="how-to-parse-a-string-visual-basic"></a>作法：剖析字串 (Visual Basic)
本主題說明如何在中C#建立 XML 樹狀結構。  
  
## <a name="example"></a>範例  
 您可以使用`XElement.Parse`方法來剖析 Visual Basic 中的字串。 不過, 使用 XML 常值會更有效率 (如下列程式碼所示), 因為 XML 常值在從字串剖析 XML 時, 不會受到相同的效能損失。  
  
 藉由使用 XML 常值, 您可以直接將 XML 複製並貼到 Visual Basic 程式中。  
  
> [!NOTE]
> 從文字檔剖析文字或載入 XML 文件比功能結構沒有效率。 如果您要從程式碼初始化 XML 樹狀，使用功能結構比剖析文字所花的處理器時間少。  
  
```vb  
Dim contacts as XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="home">206-555-0144</Phone>  
            <Phone Type="work">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type="mobile">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>  
```  
  
## <a name="see-also"></a>另請參閱

- [剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
