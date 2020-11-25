---
title: Framework 設計方針
description: 請參閱架構設計指導方針，以設計可延伸並與 .NET 互動的程式庫，以確保 API 一致性和易用性。
titleSuffix: ''
ms.date: 10/22/2008
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 03fa44c1fed219b50cf1a8d22b2c9f79947f4976
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706654"
---
# <a name="framework-design-guidelines"></a>Framework 設計方針

本節提供的指導方針可用來設計可延伸和與 .NET Framework 互動的程式庫。 其目標是要協助程式庫設計師提供統一的程式設計模型，而不受開發所用的程式設計語言，以確保 API 一致性和易用性。 建議您在開發擴充 .NET Framework 的類別和元件時，遵循這些設計指導方針。 不一致的程式庫設計對開發人員生產力和防止採用造成負面影響。  
  
 這些指導方針會組織成簡單的建議，並在前面加上條款 `Do` 、 `Consider` 、 `Avoid` 和 `Do not` 。 這些指導方針旨在協助類別庫設計人員瞭解不同解決方案之間的取捨。 在某些情況下，良好的程式庫設計可能會要求您違反這些設計指導方針。 這種情況應該很罕見，因此您一定要有清楚且吸引人的決策原因。  
  
 這些指導方針是從書籍 *架構設計指導方針中摘錄的：可重複使用之 .net 程式庫的慣例、慣用語和模式、第二版*、Krzysztof Cwalina 和 Brad Abrams。  
  
## <a name="in-this-section"></a>本節內容  

 [命名指導方針](naming-guidelines.md)  
 提供在類別庫中命名元件、命名空間、類型和成員的指導方針。  
  
 [型別設計方針](type.md)  
 提供使用靜態和抽象類別、介面、列舉、結構和其他類型的指導方針。  
  
 [成員設計方針](member.md)  
 提供設計和使用屬性、方法、函式、欄位、事件、運算子和參數的指導方針。  
  
 [擴充性設計](designing-for-extensibility.md)  
 討論擴充性機制，例如子類別化、使用事件、虛擬成員和回呼，以及說明如何選擇最符合您架構需求的機制。  
  
 [例外狀況的設計方針](exceptions.md)  
 描述設計、擲回和攔截例外狀況的設計方針。  
  
 [使用指導方針](usage-guidelines.md)  
 描述使用一般類型的指導方針，例如陣列、屬性和集合、支援序列化，以及多載等號比較運算子。  
  
 [常見的設計模式](common-design-patterns.md)  
 提供選擇和執行相依性屬性的指導方針。  
  
 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*  
  
 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。  
  
## <a name="see-also"></a>另請參閱

- [概觀](../../framework/get-started/overview.md)
- [開發指南](../../framework/development-guide.md)
