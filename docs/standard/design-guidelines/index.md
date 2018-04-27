---
title: Framework 設計方針
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c54ec4a5cc3c4bef1e6460b2c9971af4e2af983a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="framework-design-guidelines"></a>Framework 設計方針
本節提供指導方針來設計文件庫，可擴充及.NET Framework 進行互動。 目標是要協助確保應用程式開發介面一致性和易用性藉由提供統一的程式設計模型，用於開發的程式語言無關的程式庫設計工具。 我們建議您開發的類別和擴充.NET Framework 的元件時，請遵循這些設計指導方針。 不一致的程式庫設計造成不良影響開發人員生產力，並讓採用受阻。  
  
 指導方針會組織成簡單的建議前置詞條款`Do`， `Consider`， `Avoid`，和`Do not`。 這些指導方針被用來協助了解不同的方案之間的取捨類別程式庫設計工具。 可能會有良好的程式庫設計需要您違反這些設計指導方針的情況。 這種情況下應該很少見，而且您必須清除且吸引人的原因，對您的決策。  
  
 這些指導方針摘錄自活頁簿*Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式*，透過 Krzysztof Cwalina Brad Abrams。  
  
## <a name="in-this-section"></a>本節內容  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 提供的指導方針命名組件、 命名空間、 類型和成員類別庫中。  
  
 [類型設計方針](../../../docs/standard/design-guidelines/type.md)  
 提供使用靜態和抽象類別、 介面、 列舉、 結構和其他類型的方針。  
  
 [成員設計方針](../../../docs/standard/design-guidelines/member.md)  
 提供指導方針設計與使用屬性、 方法、 建構函式、 欄位、 事件、 運算子和參數。  
  
 [擴充性設計](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 討論擴充性機制，例如子類別化，使用事件、 虛擬成員和回呼，並說明如何選擇最符合您的架構需求的機制。  
  
 [例外狀況的設計方針](../../../docs/standard/design-guidelines/exceptions.md)  
 說明設計、 擲回和攔截例外狀況的設計方針。  
  
 [用法方針](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 描述如何使用常見的類型，例如陣列、 屬性和集合、 支援序列化，以及多載等號比較運算子的指導方針。  
  
 [一般設計模式](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 提供指導方針選擇，以及實作相依性屬性和的處置模式。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [概觀](../../../docs/framework/get-started/overview.md)  
 [.NET Framework 的藍圖](https://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [開發指南](../../../docs/framework/development-guide.md)
