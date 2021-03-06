---
title: "성능 최적화: 레이아웃 및 디자인"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 13763e0487314fdbe7ab6fcb8b7b8711715e7a6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-layout-and-design"></a>성능 최적화: 레이아웃 및 디자인
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 응용 프로그램의 디자인 작업은 레이아웃 계산과 개체 참조의 유효성 검사 과정에서 불필요한 오버헤드를 초래하여 성능에 영향을 줄 수 있습니다. 또한 개체 생성 작업은 특히 런타임에 응용 프로그램의 성능 특성에 영향을 줄 수 있습니다.  
  
 이 항목에서는 이러한 영역에서 성능과 관련된 권장 사항을 제공합니다.  
  
## <a name="layout"></a>레이아웃  
 측정 및의 멤버 정렬의 프로세스를 설명 하는 "레이아웃 단계" 라는 용어는 <xref:System.Windows.Controls.Panel>-파생 다음 화면에 그리는 및 자식의 개체의 컬렉션입니다. 레이아웃 단계는 많은 계산이 요구되는 프로세스이며 컬렉션의 자식 수가 많을수록 더 많은 계산이 필요합니다. 예를 들어 자식 때마다 <xref:System.Windows.UIElement> 컬렉션에 개체 변경의 위치, 레이아웃 시스템에서 새로운 패스를 트리거될 수에 있습니다. 개체 특성과 레이아웃 동작 간의 긴밀한 관계로 인해 레이아웃 시스템을 호출할 수 있는 이벤트의 형식을 이해하는 것이 중요합니다. 레이아웃 단계의 불필요한 호출을 되도록 많이 줄이면 응용 프로그램의 성능이 향상됩니다.  
  
 레이아웃 시스템은 컬렉션의 각 자식 멤버에 대해 두 개의 단계인 측정 단계 및 정렬 단계를 수행합니다. 각 자식 개체의 재정의 된 구현에 제공 된 <xref:System.Windows.UIElement.Measure%2A> 및 <xref:System.Windows.UIElement.Arrange%2A> 자체 특정 레이아웃 동작을 제공 하기 위해 메서드. 가장 간단한 레이아웃은 화면에서 크기 조정, 배치 및 그리기를 수행할 요소가 되는 재귀 시스템입니다.  
  
-   자식 <xref:System.Windows.UIElement> 먼저 핵심 속성이 측정 하 여 개체 레이아웃 프로세스를 시작 합니다.  
  
-   개체의 <xref:System.Windows.FrameworkElement> 크기와 같은 관련 된 속성을 <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, 및 <xref:System.Windows.FrameworkElement.Margin%2A>, 평가 됩니다.  
  
-   <xref:System.Windows.Controls.Panel>-와 같은 특정 논리가 적용 되며는 <xref:System.Windows.Controls.DockPanel.Dock%2A> 속성의는 <xref:System.Windows.Controls.DockPanel>, 또는 <xref:System.Windows.Controls.StackPanel.Orientation%2A> 의 속성은 <xref:System.Windows.Controls.StackPanel>합니다.  
  
-   모든 자식 개체가 측정된 후 콘텐츠가 정렬 또는 배치됩니다.  
  
-   자식 개체의 컬렉션이 화면에 그려집니다.  
  
 다음 작업 중 하나가 발생할 경우 레이아웃 단계 프로세스가 다시 호출됩니다.  
  
-   자식 개체가 컬렉션에 추가됩니다.  
  
-   A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 자식 개체에 적용 됩니다.  
  
-   <xref:System.Windows.UIElement.UpdateLayout%2A> 자식 개체에 대 한 메서드 호출 됩니다.  
  
-   측정 또는 정렬 단계에 영향을 주는 메타데이터로 표시된 종속성 속성의 값에 변경이 발생할 경우  
  
### <a name="use-the-most-efficient-panel-where-possible"></a>가능한 경우 가장 효율적인 패널 사용  
 레이아웃 프로세스의 복잡성은 레이아웃 동작에 따라 직접는 <xref:System.Windows.Controls.Panel>-사용 하는 요소를 파생 합니다. 예를 들어는 <xref:System.Windows.Controls.Grid> 또는 <xref:System.Windows.Controls.StackPanel> 보다 훨씬 더 많은 기능을 제공 하는 컨트롤을 <xref:System.Windows.Controls.Canvas> 제어 합니다. 기능이 많이 제공될수록 성능 비용이 증가합니다. 그러나는 기능이 필요 하지 않은 경우 하 한 <xref:System.Windows.Controls.Grid> 컨트롤에서 제공와 같은 보다 저렴 한 비용 대안을 사용 해야는 <xref:System.Windows.Controls.Canvas> 또는 사용자 지정 패널입니다.  
  
 자세한 내용은 [패널 개요](../../../../docs/framework/wpf/controls/panels-overview.md)를 참조하세요.  
  
### <a name="update-rather-than-replace-a-rendertransform"></a>RenderTransform을 대체하는 대신 업데이트  
 업데이트할 수 있습니다는 <xref:System.Windows.Media.Transform> 의 값으로 대체 하는 대신는 <xref:System.Windows.UIElement.RenderTransform%2A> 속성입니다. 애니메이션과 관련된 시나리오가 특히 이러한 경우에 해당합니다. 기존 업데이트 하 여 <xref:System.Windows.Media.Transform>, 불필요 한 레이아웃 계산이 시작 되지 않습니다.  
  
### <a name="build-your-tree-top-down"></a>하향식 트리 빌드  
 논리적 트리에서 노드가 추가 또는 제거될 경우 노드의 부모 및 모든 자식에서 속성 무효화가 발생합니다. 결과적으로 이미 유효성이 검사된 노드에서 불필요한 무효화의 비용을 방지하려면 항상 하향식 생성 패턴을 따라야 합니다. 다음 표에서 하향식 및 상향식의 트리를 단일 150 수준의 트리를 작성할 실행 속도 차이 보여 줍니다. <xref:System.Windows.Controls.TextBlock> 및 <xref:System.Windows.Controls.DockPanel> 각 수준에 있습니다.  
  
|**작업**|**트리 빌드(ms)**|**렌더링—트리 빌드 포함(ms)**|  
|----------------|---------------------------------|-------------------------------------------------|  
|상향식|366|454|  
|하향식|11|96|  
  
 다음 코드 예제에서는 하향식 트리를 만드는 방법을 보여 줍니다.  
  
 [!code-csharp[Performance#PerformanceSnippet1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 논리적 트리에 대한 자세한 내용은 [WPF의 트리](../../../../docs/framework/wpf/advanced/trees-in-wpf.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [WPF 응용 프로그램 성능 최적화](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [응용 프로그램 성능 계획](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [하드웨어 이용](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [2차원 그래픽 및 이미징](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [개체 동작](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [응용 프로그램 리소스](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [데이터 바인딩](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [기타 성능 권장 사항](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [레이아웃](../../../../docs/framework/wpf/advanced/layout.md)
