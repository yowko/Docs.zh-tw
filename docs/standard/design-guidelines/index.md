---
title: Framework 設計方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df2ccf3d778e26e16937554304ae847f624cfec0
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085631"
---
# <a name="framework-design-guidelines"></a>Framework 設計方針
本章節提供指導方針來設計擴充並與其互動 .NET Framework 的程式庫。 目標是要協助確保 API 一致性和易用性，藉由提供統一的程式設計模型，用於開發的程式設計語言無關的程式庫設計人員。 我們建議您遵循這些設計指導方針，開發可擴充.NET Framework 的類別和元件時。 不一致的程式庫設計造成不良影響開發人員的生產力，並防止採用。  
  
 指導方針會編排成簡單的建議前置詞條款`Do`， `Consider`， `Avoid`，和`Do not`。 這些指導方針旨在協助類別庫設計人員了解不同方案之間的取捨。 可能會有一些情況良好的程式庫設計需要您違反這些設計指導方針。 這種情況下應該很少見，而且您必須清除且吸引人的原因，對您的決策。  
  
 這些指導方針摘錄自本書*Framework 設計方針： 慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式*，Krzysztof Cwalina 與 Brad Abrams。  
  
## <a name="in-this-section"></a>本節內容  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 提供的指導方針命名組件、 命名空間、 類型和類別庫中的成員。  
  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
 提供使用靜態和抽象類別、 介面、 列舉、 結構與其他類型的指導方針。  
  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
 提供設計和使用屬性、 方法、 建構函式、 欄位、 事件、 運算子和參數的指導方針。  
  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 討論擴充性機制，例如子類別化，使用事件、 虛擬成員和回呼，並說明如何選擇最符合您的架構需求的機制。  
  
 [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)  
 說明設計、 擲回和攔截例外狀況的設計方針。  
  
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 描述使用常見的類型，例如陣列、 屬性和集合、 支援序列化，以及多載等號比較運算子的指導方針。  
  
 [一般設計模式](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 提供指導方針選擇並實作相依性屬性和處置模式。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [概觀](../../../docs/framework/get-started/overview.md)  
- [.NET Framework 藍圖](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
- [開發指南](../../../docs/framework/development-guide.md)
