---
title: 擴充性設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: KrzysztofCwalina
ms.openlocfilehash: 94900dee72230a1b9d099d78168acc508af62af7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127351"
---
# <a name="designing-for-extensibility"></a>擴充性設計
設計一套架構的一個重要層面確保已仔細考慮擴充性的 framework。 這需要您了解各種擴充性機制相關聯的優點與成本。 此章節可協助您決定哪一種的擴充性機制，子類別化、 事件、 虛擬成員、 回呼和等等 — 可以最符合您的架構需求。  
  
 有許多方法可允許擴充性架構中。 它們範圍權力較小，但成本更低但昂貴的功能非常強大。 任何指定的擴充性需求，您應該選擇符合需求的最低成本高擴充性機制。 請記住，通常可以稍後新增更多的擴充性，但您絕對不能它立即且不會造成重大變更。  
  
## <a name="in-this-section"></a>本節內容  
 [非密封類別](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Protected 成員](../../../docs/standard/design-guidelines/protected-members.md)  
 [事件和回呼](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [虛擬成員](../../../docs/standard/design-guidelines/virtual-members.md)  
 [抽象 (抽象類型和介面)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [實作抽象的基底類別](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [密封](../../../docs/standard/design-guidelines/sealing.md)  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
