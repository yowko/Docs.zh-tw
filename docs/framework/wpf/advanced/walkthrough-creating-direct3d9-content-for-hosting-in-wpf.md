---
title: 逐步解說：建立裝載於 WPF 中的 Direct3D9 內容
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- WPF [WPF], creating Direct3D9 content
- Direct3D9 [WPF interoperability], creating Direct3D9 content
ms.assetid: 286e98bc-1eaa-4b5e-923d-3490a9cca5fc
ms.openlocfilehash: 321c4ba8659bd2226fff96e74e81ef24f0077c3d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200910"
---
# <a name="walkthrough-creating-direct3d9-content-for-hosting-in-wpf"></a>逐步解說：建立裝載於 WPF 中的 Direct3D9 內容
本逐步解說示範如何建立適用於 Windows Presentation Foundation (WPF) 應用程式中裝載 Direct3D9 內容。 如需有關裝載 WPF 應用程式中的 Direct3D9 內容的詳細資訊，請參閱[WPF 和 Direct3D9 互通](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md)。

 在這個逐步解說中，您將執行下列工作：

-   建立 Direct3D9 專案。

-   設定 WPF 應用程式中裝載 Direct3D9 專案。

 當您完成時，您必須包含用於在 WPF 應用程式中的 Direct3D9 內容的 DLL。

## <a name="prerequisites"></a>必要條件
 您需要下列元件才能完成此逐步解說：

-   Visual Studio 2010。

-   DirectX SDK 9or 更新版本。

## <a name="creating-the-direct3d9-project"></a>建立 Direct3D9 專案
 第一個步驟是建立和設定 Direct3D9 專案。

#### <a name="to-create-the-direct3d9-project"></a>若要建立 Direct3D9 專案

1.  名為 c + + 中建立新的 Win32 專案`D3DContent`。

     Win32 應用程式精靈 隨即開啟，並顯示歡迎畫面。

2.  按 [ **下一步**]。

     [應用程式設定] 畫面隨即出現。

3.  在 **應用程式類型：** 區段中，選取**DLL**選項。

4.  按一下 [ **完成**]。

     會產生 D3DContent 專案。

5.  在 方案總管 中，以滑鼠右鍵按一下 D3DContent 專案，然後選取**屬性**。

     **D3DContent 屬性頁**對話方塊隨即開啟。

6.  選取  **C/c + +** 節點。

7.  在 **其他 Include 目錄**欄位中，指定的 DirectX 位置包含的資料夾。 此資料夾的預設位置是 %ProgramFiles%\Microsoft DirectX SDK (*版本*) \Include。

8.  按兩下**連結器**節點來展開它。

9. 在 **其他程式庫目錄**欄位中，指定 DirectX 程式庫資料夾的位置。 此資料夾的預設位置是 %ProgramFiles%\Microsoft DirectX SDK (*版本*) \Lib\x86。

10. 選取 **輸入**節點。

11. 在 **其他相依性**欄位中，新增`d3d9.lib`和`d3dx9.lib`檔案。

12. 在 [方案總管] 中，加入新模組定義檔 (.def) 名為`D3DContent.def`至專案。

## <a name="creating-the-direct3d9-content"></a>建立 Direct3D9 內容
 若要取得最佳效能，Direct3D9 內容必須使用特定的設定。 下列程式碼示範如何建立具有最佳的效能特性的 Direct3D9 介面。 如需詳細資訊，請參閱 < [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)。

#### <a name="to-create-the-direct3d9-content"></a>建立 Direct3D9 內容

1.  使用 [方案總管] 中，加入名為下列專案的三個 c + + 類別。

     `CRenderer` （含虛擬的解構函式）

     `CRendererManager`

     `CTriangleRenderer`

2.  在程式碼編輯器中開啟 Renderer.h，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.h#rendererh)]

3.  在程式碼編輯器中開啟 Renderer.cpp，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderercpp)]

4.  在程式碼編輯器中開啟 RendererManager.h，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.h#renderermanagerh)]

5.  在程式碼編輯器中開啟 RendererManager.cpp，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#RendererManagerCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanagercpp)]

6.  在程式碼編輯器中開啟 TriangleRenderer.h，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.h#trianglerendererh)]

7.  在程式碼編輯器中開啟 TriangleRenderer.cpp，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#TriangleRendererCPP](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/trianglerenderer.cpp#trianglerenderercpp)]

8.  在程式碼編輯器中開啟 stdafx.h，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#StdafxH](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/stdafx.h#stdafxh)]

9. 在程式碼編輯器中開啟 dllmain.cpp，並以下列程式碼取代自動產生的程式碼。

     [!code-cpp[System.Windows.Interop.D3DImage#DllMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/dllmain.cpp#dllmain)]

10. 在程式碼編輯器中開啟 D3DContent.def。

11. 下列程式碼取代自動產生的程式碼。

    ```
    LIBRARY "D3DContent"

    EXPORTS

    SetSize
    SetAlpha
    SetNumDesiredSamples
    SetAdapter

    GetBackBufferNoRef
    Render
    Destroy
    ```

12. 建置專案。

## <a name="next-steps"></a>後續步驟

-   裝載 Direct3D9 內容，在 WPF 應用程式。 如需詳細資訊，請參閱 <<c0> [ 逐步解說： 裝載 Direct3D9 內容在 WPF 中](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Interop.D3DImage>
- [Direct3D9 和 WPF 互通性的效能考量](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
- [逐步解說：在 WPF 中裝載 Direct3D9 內容](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)