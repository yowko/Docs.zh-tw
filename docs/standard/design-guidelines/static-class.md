---
title: 靜態類別設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92152600d317c04e3fef26400b11e94a549fde4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571055"
---
# <a name="static-class-design"></a>靜態類別設計
靜態類別會定義為只包含靜態成員的類別 (當然除了繼承自執行個體成員<xref:System.Object?displayProperty=nameWithType>和可能的私用的建構函式)。 某些語言提供靜態類別內建支援。 C# 2.0 版及更新版本中，類別會宣告為靜態，當它是密封、 抽象的而且可以覆寫或宣告沒有任何執行個體成員。  
  
 靜態類別是單純的物件導向設計和簡單性之間的洩露。 它們通常用來提供其他作業的快速鍵 (例如<xref:System.IO.File?displayProperty=nameWithType>)，擴充方法或功能的完整物件導向包裝函式為未經授權的持有者 (例如<xref:System.Environment?displayProperty=nameWithType>)。  
  
 **✓ DO** 謹慎使用靜態類別。  
  
 靜態類別應作為只支援物件導向的核心架構的類別。  
  
 **X DO NOT** 視為其他的值區的靜態類別。  
  
 **X DO NOT** 宣告或覆寫在靜態類別中的執行個體成員。  
  
 **✓ DO** 宣告為密封，抽象的並加入私用執行個體建構函式，如果您的程式語言並沒有內建支援靜態類別。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
