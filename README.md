# How to customize style of the scroll viewer in WPF DataGrid (SfDataGrid)
 
## Customize style of the scroll viewer
You can customize the style of scroll viewer in which WPF DataGrid (SfDataGrid) is loaded. But while scrolling using mouse wheel, the header will also be scrolled with records. You can overcome this behavior by binding the CanContentScroll property of ScrollViewer.

## XAML:

```XAML

<Window.Resources>
  <Style TargetType="ScrollViewer">
    <Setter Property="Template">
      <Setter.Value>
         <ControlTemplate TargetType="ScrollViewer">
           <Border CornerRadius="2" 
                   BorderBrush="{TemplateBinding BorderBrush}"  
                   BorderThickness="{TemplateBinding BorderThickness}">
              <Grid Background="{TemplateBinding Background}">
                <Grid.RowDefinitions>
                   <RowDefinition Height="*"/>
                   <RowDefinition Height="Auto"/>
                </Grid.RowDefinitions>
                <Grid.ColumnDefinitions>
                   <ColumnDefinition Width="*"/>
                   <ColumnDefinition Width="Auto"/>
                </Grid.ColumnDefinitions>
 
                <ScrollContentPresenter x:Name="ScrollContentPresenter"
                      CanContentScroll="{TemplateBinding CanContentScroll}"
                      Cursor="{TemplateBinding Cursor}"
                      Margin="{TemplateBinding Padding}"
                      ContentTemplate="{TemplateBinding ContentTemplate}"/>
 
                <Rectangle Grid.Column="1" Grid.Row="1" Fill="#FFE9EEF4"/>
 
                <ScrollBar x:Name="VerticalScrollBar" Width="18" IsTabStop="False"
                     Visibility="{TemplateBinding ComputedVerticalScrollBarVisibility}"
                     Grid.Column="1" Grid.Row="0" Orientation="Vertical"
                     ViewportSize="{TemplateBinding ViewportHeight}"
                     Maximum="{TemplateBinding ScrollableHeight}"
                     Minimum="0"
                     Value="{TemplateBinding VerticalOffset}"
                     Margin="0,-1,-1,-1"/>
 
                <ScrollBar x:Name="HorizontalScrollBar" Height="18" IsTabStop="False"
                   Visibility="{TemplateBinding ComputedHorizontalScrollBarVisibility}"
                   Grid.Column="0" Grid.Row="1" Orientation="Horizontal"
                   ViewportSize="{TemplateBinding ViewportWidth}"
                   Maximum="{TemplateBinding ScrollableWidth}"
                   Minimum="0"
                   Value="{TemplateBinding HorizontalOffset}"
                   Margin="-1,0,-1,-1"/>
 
             </Grid>
           </Border>
         </ControlTemplate>
      </Setter.Value>
    </Setter>
  </Style>
</Window.Resources>   
```
 