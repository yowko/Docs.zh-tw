---
title: "擴充性設計"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbee2fb24b9acf9bc2512b399e3a74e66720cc3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="designing-for-extensibility"></a>擴充性設計
設計一個架構的一個重要層面確保已仔細考慮架構的擴充性。 這需要您已了解的成本與利益各種擴充性機制相關聯。 本章節可協助您決定哪一個擴充性機制 — 子類別化、 事件、 虛擬成員、 回呼 (callback) 等等，可以最符合您的架構的需求。  
  
 有許多方法可允許擴充性架構中。 這些範圍較不強大，卻經濟的成本非常強大，但高度耗費資源。 對於任何給定的擴充性項需求，您應該選擇符合需求的最高擴充性機制。 請記住，若要加入更大的擴充，通常可以但是您可以永遠不會佔用它而不會引進重大變更。  
  
## <a name="in-this-section"></a>本章節內容  
 [非密封的類別](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [受保護的成員](../../../docs/standard/design-guidelines/protected-members.md)  
 [事件和回撥](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)  
 [抽象層 （抽象型別和介面）](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [實作抽象的基底類別](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [密封](../../../docs/standard/design-guidelines/sealing.md)  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
