---
title: 欄位設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
author: KrzysztofCwalina
ms.openlocfilehash: 3ab8fe279605c4795bb3a26557d0241b186b273a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690445"
---
# <a name="field-design"></a>欄位設計
封裝原則可讓其中一個最重要的概念是物件導向設計中。 此原則就是儲存在物件內的資料必須能夠存取只適用於該物件。  
  
 實用的方式來解譯原則是說應該設計為型別，以便可以對進行變更 （名稱或類型的變更） 該類型的欄位，而不會中斷程式碼以外之成員的型別。 此解譯立即表示所有欄位必須都是私用。  
  
 因為這類欄位中，幾乎是根據定義，永遠不需要變更，我們可以排除從這個嚴格限制的常數和靜態唯讀欄位。  
  
 **X DO NOT** 提供公用或受保護的執行個體欄位。  
  
 您應該提供屬性存取欄位，而不是公用或受保護，請將它們。  
  
 **✓ DO** 常數欄位使用的常數，永遠不會變更。  
  
 編譯器會燒壞 const 欄位的值，直接在呼叫程式碼。 因此，可以永遠不會變更常數的值，而不需要中斷相容性的風險。  
  
 **✓ DO** 使用公用靜態 `readonly` 預先定義的物件執行個體的欄位。  
  
 如果有預先定義的類型執行個體，請將它們宣告為公用唯讀靜態欄位的型別本身。  
  
 **X DO NOT** 指派到可變動類型的執行個體 `readonly` 欄位。  
  
 可變動的型別是可以執行個體化之後進行修改的執行個體的類型。 例如，陣列、 大多數的集合和資料流是可變動的型別，但<xref:System.Int32?displayProperty=nameWithType>， <xref:System.Uri?displayProperty=nameWithType>，和<xref:System.String?displayProperty=nameWithType>全都是不變。 參考型別欄位上的唯讀修飾詞會防止執行個體儲存在欄位中，從已經被取代，但它無法防止呼叫成員變更的執行個體正在修改欄位的執行個體資料。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [成員設計方針](../../../docs/standard/design-guidelines/member.md)
- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
