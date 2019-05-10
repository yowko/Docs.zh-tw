---
title: HOW TO：調整 Windows Forms 大小
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
ms.openlocfilehash: aa7ee2bbbf6983a371ea71edc0dfd0cc12cd0c9d
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211658"
---
# <a name="how-to-resize-windows-forms"></a>HOW TO：調整 Windows Forms 大小

您可以使用幾種方式來指定 Windows Form 的大小。 您可以為 <xref:System.Windows.Forms.Form.Size%2A> 屬性設定新值，或個別調整 <xref:System.Windows.Forms.Control.Height%2A> 或 <xref:System.Windows.Forms.Control.Width%2A> 屬性，以程式設計方式來變更表單的高度和寬度。 如果您使用 Visual Studio，您可以變更使用 Windows Form 設計工具的大小。 另請參閱[How to:調整 Windows Form 使用設計工具的大小](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/37k2zkwx(v=vs.100))。

## <a name="resize-a-form-programmatically"></a>以程式設計方式調整表單的大小

設定表單的 <xref:System.Windows.Forms.Form.Size%2A> 屬性，在執行階段定義表單的大小。

下列程式碼範例示範將表單大小設定為 100 × 100 像素。

```vb
Form1.Size = New System.Drawing.Size(100, 100)
```

```csharp
Form1.Size = new System.Drawing.Size(100, 100);
```

```cpp
Form1->Size = System::Drawing::Size(100, 100);
```

## <a name="change-form-width-and-height-programmatically"></a>以程式設計方式變更表單寬度和高度

定義 <xref:System.Windows.Forms.Form.Size%2A> 之後，使用 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 屬性來變更表單高度或寬度。

下列程式碼範例示範將表單的寬度設定為 300 像素 (從表單的左邊緣算起)，而高度則維持不變。

```vb
Form1.Width = 300
```

```csharp
Form1.Width = 300;
```

```cpp
Form1->Width = 300;
```

-或-

設定 <xref:System.Windows.Forms.Form.Size%2A> 屬性來變更 <xref:System.Drawing.Size.Width%2A> 或 <xref:System.Drawing.Size.Height%2A>。

不過，如下列程式碼範例所示，這種方法比直接設定 <xref:System.Windows.Forms.Control.Width%2A> 或 <xref:System.Windows.Forms.Control.Height%2A> 屬性更困難。

```vb
Form1.Size = New Size(300, Form1.Size.Height)
```

```csharp
Form1.Size = new Size(300, Form1.Size.Height);
```

```cpp
Form1->Size = System::Drawing::Size(300, Form1->Size.Height);
```

## <a name="change-form-size-by-increments-programmatically"></a>以程式設計方式遞增變更表單大小

若要遞增表單的大小，請設定 <xref:System.Drawing.Size.Width%2A> 和 <xref:System.Drawing.Size.Height%2A> 屬性。

下列程式碼範例示範將表單的寬度設定為比目前設定還要寬 200 像素。

```vb
Form1.Width += 200
```

```csharp
Form1.Width += 200;
```

```cpp
Form1->Width += 200;
```

> [!CAUTION]
> 除非您透過將 <xref:System.Windows.Forms.Form.Size%2A> 屬性設定為新的 <xref:System.Drawing.Size> 結構，來同時設定高度和寬度維度，否則請一律使用 <xref:System.Drawing.Size.Height%2A> 或 <xref:System.Drawing.Size.Width%2A> 屬性來變更表單的維度。 <xref:System.Windows.Forms.Form.Size%2A> 屬性會傳回實值類型的 <xref:System.Drawing.Size> 結構。 您無法指派新值給實值類型的屬性。 因此，下列程式碼範例將無法進行編譯。

```vb
' NOTE: CODE WILL NOT COMPILE
Dim f As New Form()
f.Size.Width += 100
```

```csharp
// NOTE: CODE WILL NOT COMPILE
Form f = new Form();
f.Size.Width += 100;
```

```cpp
// NOTE: CODE WILL NOT COMPILE
Form^ f = gcnew Form();
f->Size->X += 100;
```

## <a name="see-also"></a>另請參閱

- [Windows Forms 使用者入門](getting-started-with-windows-forms.md)
- [增強 Windows Forms 應用程式](./advanced/index.md)
