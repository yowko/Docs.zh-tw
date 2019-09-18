---
title: x:Members 指示詞
ms.date: 03/30/2017
ms.assetid: 155b393d-3b49-4c5a-8c9e-b3d9893af4e4
ms.openlocfilehash: ca42079c1c40a8fb3b1ddfc8f4a6f742768fa9e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053760"
---
# <a name="xmembers-directive"></a>x:Members 指示詞
保留一組定義于標記中的成員，其適用于父元素的 X：Class。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Class="className">  
  <x:Members>  
    oneOrMoreMembers  
  </x:Members  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`className`|XAML 生產的支援類別或部分類別名稱。 請參閱＜備註＞。|  
|`oneOrMoreMembers`|一或多個代表成員定義的物件元素。 一般而言，這些是`x:Property`物件元素。 請參閱＜備註＞。|  
  
## <a name="remarks"></a>備註  
 在 .NET Framework XAML 服務執行中，沒有的`x:Members`支援類別或基礎成員執行。 `x:Members`是特殊的 XAML 成員，可以在任何類型上當做成員存在。 在 xaml 節點資料流程中， `x:Members`會以 xaml 語言 xaml 命名`Members`空間中名為的成員表示。 成員`Members`包含`Member`物件的唯讀泛型清單。 在一般的標記中，會將個別`x:Property`成員指定為屬性元素。 `x:Property`是更精確的類型，專門用於類型的屬性，而且可`x:Member`指派給。 如需詳細資訊，請參閱[x:Property](x-property-directive.md)指示詞。  
  
 若要支援實際使用 `x:Members` 做為在標記中指定成員定義的方法，這些成員必須與可修改的類別相關聯。 預期的模型是 `x:Members` 做為可指定 `x:Class` 之類型成員的形式存在。 不過，.NET Framework XAML 服務層級不支援關聯類型與成員或產生動態成員定義的機制。 這會保留給具有支援 XAML 成員定義之應用程式模型的個別架構。 通常需要 MSBUILD 建置動作以標記編譯 XAML，然後與程式碼後置整合，或是從 XAML 產生純組件，才能支援該功能。  
  
## <a name="xmembers-for-windows-workflow-foundation"></a>Windows Workflow Foundation 的 x:Members  
 針對 Windows Workflow Foundation， `x:Members`包含完全以 xaml 撰寫之自訂活動的成員，或是包含程式碼後置之活動設計工具的 xaml 定義動態成員。 `x:Class` 也必須在 XAML 生產的根項目上指定。 這不是 .NET Framework XAML 服務層級的需求，但是當 XAML 生產是由支援自訂活動和 Windows Workflow Foundation XAML 的 MSBUILD 建置動作載入時，通常會變成需求。 `x:Members`必須是宣告之物件元素`x:Class`標記中的第一個子專案。
