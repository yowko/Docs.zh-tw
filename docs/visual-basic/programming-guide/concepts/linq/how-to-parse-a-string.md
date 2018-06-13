---
title: 如何： 剖析字串 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
ms.openlocfilehash: da12ec98e03acceae375bbed4fc6ad4c2a71ec2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33640237"
---
# <a name="how-to-parse-a-string-visual-basic"></a>如何： 剖析字串 (Visual Basic)
本主題說明如何在 C# 中建立 XML 樹狀結構。  
  
## <a name="example"></a>範例  
 您可以在 Visual Basic 中的將字串剖析使用`XElement.Parse`方法。 不過，它是使用 XML 常值，如下列程式碼所示，因為 XML 常值不會發生相同的效能低落，從字串剖析 XML 更有效率。  
  
 藉由使用 XML 常值，您可以只複製並貼入您的 Visual Basic 程式中的 XML。  
  
> [!NOTE]
>  從文字檔剖析文字或載入 XML 文件比功能結構沒有效率。 如果您要從程式碼初始化 XML 樹狀，使用功能結構比剖析文字所花的處理器時間少。  
  
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
 [剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
