---
title: 抽象 (抽象類型和介面)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5863b4ae9cad940e4dd47ef93e07763916427f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573022"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>抽象 (抽象類型和介面)
抽象概念是描述合約，但不提供完整的實作的合約的型別。 抽象概念通常會實作為抽象類別或介面，和它們隨附一組妥善定義的參考文件描述的實作合約的型別所需的語意。 某些.NET Framework 中最重要的抽象概念包括<xref:System.IO.Stream>， <xref:System.Collections.Generic.IEnumerable%601>，和<xref:System.Object>。  
  
 您可以透過實作支援抽象的合約的具象型別，並使用 framework 應用程式開發介面使用 （操作） 此具象型別擴充架構的抽象概念。  
  
 有意義且實用的抽象概念，能夠承受，測試是時間的很難設計。 主要的難度即將不再和不較少的成員權限集。 如果抽象概念，具有太多的成員，它會變成難以或甚至無法實作。 如果有太少的成員，承諾的功能，它會變成無效，在許多有趣的情況下。  
  
 太多的抽象概念，在架構中也有負面影響架構的可用性。 通常是很難了解如果不了解它如何融入的具象實作和操作資料的抽象 Api 較大的圖片的抽象概念。 此外，抽象概念和其成員的名稱是抽象的這樣會使得它們隱晦且親近不含第一個的了解其使用方式的更廣泛的內容。  
  
 不過，抽象層提供極為強大的其他擴充性機制無法通常會比對的擴充性。 它們是許多架構模式的詳細資訊，例如外掛程式，核心逆轉控制 (IoC)、 管線等等。 它們也是極為重要的測試能力的架構。 良好的抽象概念實現出大量的相依性，以便進行單元測試虛設常式。 總而言之，抽象化是負責 sought-after 現代化的物件導向架構的豐富。  
  
 **X DO NOT** 提供抽象，除非它們經過開發數種具象實作和應用程式開發介面使用的抽象概念。  
  
 **✓ DO** 設計抽象時請小心選擇之間的抽象類別和介面。  
  
 **✓ CONSIDER** 提供參考測試的具象實作的抽象概念。 這類測試應該允許使用者以測試是否有其正確實作的合約。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
