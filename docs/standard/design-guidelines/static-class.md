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
author: KrzysztofCwalina
ms.openlocfilehash: d0a2f11b53f50f2ec2f301f7b88df65e1cd7b811
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762042"
---
# <a name="static-class-design"></a>靜態類別設計
靜態類別會定義為只包含靜態成員的類別 (當然除了繼承自的執行個體成員<xref:System.Object?displayProperty=nameWithType>和可能的私用的建構函式)。 某些語言中提供靜態類別的內建的支援。 在 C# 2.0 和更新版本中，當類別宣告為靜態，它是密封的抽象，而且可以覆寫或宣告任何執行個體成員。  
  
 靜態類別都是單純的物件導向設計和簡易性之間取得折衷。 它們通常用來提供其他作業的捷徑 (例如<xref:System.IO.File?displayProperty=nameWithType>)，擴充方法，或功能的完整物件導向包裝函式的非預期的持有者 (例如<xref:System.Environment?displayProperty=nameWithType>)。  
  
 **✓ DO** 謹慎使用靜態類別。  
  
 靜態類別應該僅被用作為支援物件導向的核心架構的類別。  
  
 **X DO NOT** 視為其他的值區的靜態類別。  
  
 **X DO NOT** 宣告或覆寫在靜態類別中的執行個體成員。  
  
 **✓ DO** 宣告為密封，抽象的並加入私用執行個體建構函式，如果您的程式語言並沒有內建支援靜態類別。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [類型設計方針](../../../docs/standard/design-guidelines/type.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
