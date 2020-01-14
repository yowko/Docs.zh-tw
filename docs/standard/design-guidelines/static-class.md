---
title: 靜態類別設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 35bcf1d403c78cdfcbb476b2eb5de2251a564b9a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709058"
---
# <a name="static-class-design"></a>靜態類別設計
靜態類別定義為僅包含靜態成員的類別（當然，除了繼承自 <xref:System.Object?displayProperty=nameWithType> 的實例成員之外，可能也會是私用的函數）。 某些語言會提供靜態類別的內建支援。 在C# 2.0 和更新版本中，將類別宣告為靜態時，它是密封的、抽象的，而且不能覆寫或宣告任何實例成員。  
  
 靜態類別是單純的物件導向設計與簡單的取捨。 它們通常用來提供其他作業的快捷方式（例如 <xref:System.IO.File?displayProperty=nameWithType>）、擴充方法的持有者，或預期完整物件導向包裝函式的功能（例如 <xref:System.Environment?displayProperty=nameWithType>）。  
  
 **✓ DO**謹慎使用靜態類別。  
  
 靜態類別只能當做架構物件導向核心的支援類別使用。  
  
 **X 不會**將靜態類別視為其他值區。  
  
 **X 不會**宣告或覆寫靜態類別中的實例成員。  
  
 如果您的程式設計語言沒有靜態類別的內建支援，則**✓**會將靜態類別宣告為 sealed、abstract，並加入私用實例的函式。  
  
 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
