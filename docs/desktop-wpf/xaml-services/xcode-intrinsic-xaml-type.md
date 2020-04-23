---
title: x:Code 內建 XAML 類型
ms.date: 03/30/2017
f1_keywords:
- Code
- x:Code
- xCode
helpviewer_keywords:
- Code directive in XAML [XAML Services]
- x:Code XAML directive element [XAML Services]
- XAML [XAML Services], x:Code directive element
ms.assetid: 87986b13-1a2e-4830-ae36-15f9dc5629e8
ms.openlocfilehash: 4da72ed630c1df001e3fd6c7e55f866b94c4d9b1
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071553"
---
# <a name="xcode-intrinsic-xaml-type"></a>x:Code 內建 XAML 類型
允許在 XAML 生產中放置代碼。 此類代碼可以由編譯 XAML 的任何 XAML 處理器實現編譯,也可以保留在 XAML 生產中供以後使用,例如運行時的解釋。

## <a name="xaml-object-element-usage"></a>XAML 物件項目用法

```xaml
<x:Code>
   // code instructions, usually enclosed by CDATA...
</x:Code>
```

## <a name="remarks"></a>備註

`x:Code` XAML 指令元素中的代碼仍在常規 XML 命名空間和提供的 XAML 命名空間中解釋。 因此,通常需要將用於段`x:Code`內的代碼封閉`CDATA`。

`x:Code`不允許 XAML 生產的所有可能部署機制。 在特定框架(例如 WPF)中,必須編譯代碼。 在其他框架中,`x:Code`通常可能不允許使用。

對於允許託管`x:Code`內容的框架,用於`x:Code`內容的正確語言編譯器由用於編譯應用程式的包含專案的設置和目標確定。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

`x:Code`為 WPF 聲明的代碼有幾個值得注意的限制:

- 指令`x:Code`元素必須是 XAML 生產根元素的即時子元素。

- [x:類指令](xclass-directive.md)必須在父根元素上提供。

- 將位於其中`x:Code`的代碼通過編譯處理為已為該 XAML 頁創建的部分類的範圍。 因此,您定義的所有代碼都必須是該部分類的成員或變數。

- 除了在部分類中嵌套類(允許嵌套,但它不是典型的,因為嵌套類無法在 XAML 中引用),因此無法定義其他類。 不能定義或添加到現有部分類的命名空間以外的 CLR 命名空間。

- 對部分類 CLR 命名空間外的代碼實體的引用都必須完全限定。 如果聲明的成員是覆蓋到部分類重寫成員,則必須使用特定於語言的重寫關鍵字指定此參數。 如果在作用網域`x:Code`中 聲明的成員與從 XAML 創建的部分類的成員發生衝突,編譯器報告衝突的方式,XAML 檔無法編譯或載入。

## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](xclass-directive.md)
- [WPF 中的程式碼後置和 XAML](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [XAML 概觀 (WPF)](../fundamentals/xaml.md)
