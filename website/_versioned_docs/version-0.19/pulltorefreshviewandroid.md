---
id: version-0.19-pulltorefreshviewandroid
original_id: pulltorefreshviewandroid
title: pulltorefreshviewandroid
---
<a id="content"></a><h1>PullToRefreshViewAndroid</h1><div><div><p>React view that supports a single scrollable child view (e.g. <code>ScrollView</code>). When this child
view is at <code>scrollY: 0</code>, swiping down triggers an <code>onRefresh</code> event.</p><p>The style <code>{flex: 1}</code> might be required to ensure the expected behavior of the child component
(e.g. when the child is expected to scroll with <code>ScrollView</code> or <code>ListView</code>).</p></div><h3><a class="anchor" name="props"></a><a class="edit-github" href="https://github.com/facebook/react-native/blob/master/Libraries/PullToRefresh/PullToRefreshViewAndroid.android.js">Edit on GitHub</a>Props <a class="hash-link" href="#props">#</a></h3><div class="props"><div class="prop"><h4 class="propTitle"><a class="anchor" name="view"></a><a href="view.html#props">View props...</a> <a class="hash-link" href="#view">#</a></h4></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="colors"></a>colors <span class="propType">[ColorPropType]</span> <a class="hash-link" href="#colors">#</a></h4><div><p>The colors (at least one) that will be used to draw the refresh indicator</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="enabled"></a>enabled <span class="propType">bool</span> <a class="hash-link" href="#enabled">#</a></h4><div><p>Whether the pull to refresh functionality is enabled</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="progressbackgroundcolor"></a>progressBackgroundColor <span class="propType">ColorPropType</span> <a class="hash-link" href="#progressbackgroundcolor">#</a></h4><div><p>The background color of the refresh indicator</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="refreshing"></a>refreshing <span class="propType">bool</span> <a class="hash-link" href="#refreshing">#</a></h4><div><p>Whether the view should be indicating an active refresh</p></div></div><div class="prop"><h4 class="propTitle"><a class="anchor" name="size"></a>size <span class="propType">RefreshLayoutConsts.SIZE.DEFAULT</span> <a class="hash-link" href="#size">#</a></h4><div><p>Size of the refresh indicator, see PullToRefreshViewAndroid.SIZE</p></div></div></div></div><div><h3><a class="anchor" name="examples"></a><a class="edit-github" href="https://github.com/facebook/react-native/blob/master/Examples/UIExplorer/PullToRefreshViewAndroidExample.android.js">Edit on GitHub</a>Examples <a class="hash-link" href="#examples">#</a></h3><div class="prism language-javascript"><span class="token string">'use strict'</span><span class="token punctuation">;</span>

const React <span class="token operator">=</span> <span class="token function">require<span class="token punctuation">(</span></span><span class="token string">'react-native'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
const <span class="token punctuation">{</span>
  ScrollView<span class="token punctuation">,</span>
  StyleSheet<span class="token punctuation">,</span>
  PullToRefreshViewAndroid<span class="token punctuation">,</span>
  Text<span class="token punctuation">,</span>
  TouchableWithoutFeedback<span class="token punctuation">,</span>
  View<span class="token punctuation">,</span>
<span class="token punctuation">}</span> <span class="token operator">=</span> React<span class="token punctuation">;</span>

const styles <span class="token operator">=</span> StyleSheet<span class="token punctuation">.</span><span class="token function">create<span class="token punctuation">(</span></span><span class="token punctuation">{</span>
  row<span class="token punctuation">:</span> <span class="token punctuation">{</span>
    borderColor<span class="token punctuation">:</span> <span class="token string">'grey'</span><span class="token punctuation">,</span>
    borderWidth<span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
    padding<span class="token punctuation">:</span> <span class="token number">20</span><span class="token punctuation">,</span>
    backgroundColor<span class="token punctuation">:</span> <span class="token string">'#3a5795'</span><span class="token punctuation">,</span>
    margin<span class="token punctuation">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  text<span class="token punctuation">:</span> <span class="token punctuation">{</span>
    alignSelf<span class="token punctuation">:</span> <span class="token string">'center'</span><span class="token punctuation">,</span>
    color<span class="token punctuation">:</span> <span class="token string">'#fff'</span><span class="token punctuation">,</span>

  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  layout<span class="token punctuation">:</span> <span class="token punctuation">{</span>
    flex<span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  scrollview<span class="token punctuation">:</span> <span class="token punctuation">{</span>
    flex<span class="token punctuation">:</span> <span class="token number">1</span><span class="token punctuation">,</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

const Row <span class="token operator">=</span> React<span class="token punctuation">.</span><span class="token function">createClass<span class="token punctuation">(</span></span><span class="token punctuation">{</span>
  _onClick<span class="token punctuation">:</span> <span class="token keyword">function</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">this</span><span class="token punctuation">.</span>props<span class="token punctuation">.</span><span class="token function">onClick<span class="token punctuation">(</span></span><span class="token keyword">this</span><span class="token punctuation">.</span>props<span class="token punctuation">.</span>data<span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  render<span class="token punctuation">:</span> <span class="token keyword">function</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token punctuation">(</span>
     &lt;TouchableWithoutFeedback onPress<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>_onClick<span class="token punctuation">}</span> <span class="token operator">&gt;</span>
        &lt;View style<span class="token operator">=</span><span class="token punctuation">{</span>styles<span class="token punctuation">.</span>row<span class="token punctuation">}</span><span class="token operator">&gt;</span>
          &lt;Text style<span class="token operator">=</span><span class="token punctuation">{</span>styles<span class="token punctuation">.</span>text<span class="token punctuation">}</span><span class="token operator">&gt;</span>
            <span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>props<span class="token punctuation">.</span>data<span class="token punctuation">.</span>text <span class="token operator">+</span> <span class="token string">' ('</span> <span class="token operator">+</span> <span class="token keyword">this</span><span class="token punctuation">.</span>props<span class="token punctuation">.</span>data<span class="token punctuation">.</span>clicks <span class="token operator">+</span> <span class="token string">' clicks)'</span><span class="token punctuation">}</span>
          &lt;<span class="token operator">/</span>Text<span class="token operator">&gt;</span>
        &lt;<span class="token operator">/</span>View<span class="token operator">&gt;</span>
    &lt;<span class="token operator">/</span>TouchableWithoutFeedback<span class="token operator">&gt;</span>
    <span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
const PullToRefreshViewAndroidExample <span class="token operator">=</span> React<span class="token punctuation">.</span><span class="token function">createClass<span class="token punctuation">(</span></span><span class="token punctuation">{</span>
  statics<span class="token punctuation">:</span> <span class="token punctuation">{</span>
    title<span class="token punctuation">:</span> <span class="token string">'&lt;PullToRefreshViewAndroid&gt;'</span><span class="token punctuation">,</span>
    description<span class="token punctuation">:</span> <span class="token string">'Container that adds pull-to-refresh support to its child view.'</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>

  <span class="token function">getInitialState<span class="token punctuation">(</span></span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token punctuation">{</span>
      isRefreshing<span class="token punctuation">:</span> <span class="token boolean">false</span><span class="token punctuation">,</span>
      loaded<span class="token punctuation">:</span> <span class="token number">0</span><span class="token punctuation">,</span>
      rowData<span class="token punctuation">:</span> Array<span class="token punctuation">.</span><span class="token function">from<span class="token punctuation">(</span></span><span class="token keyword">new</span> <span class="token class-name">Array</span><span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">map<span class="token punctuation">(</span></span>
        <span class="token punctuation">(</span>val<span class="token punctuation">,</span> i<span class="token punctuation">)</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token punctuation">(</span><span class="token punctuation">{</span>text<span class="token punctuation">:</span> <span class="token string">'Initial row'</span> <span class="token operator">+</span> i<span class="token punctuation">,</span> clicks<span class="token punctuation">:</span> <span class="token number">0</span><span class="token punctuation">}</span><span class="token punctuation">)</span>
      <span class="token punctuation">)</span><span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>

  <span class="token function">_onClick<span class="token punctuation">(</span></span>row<span class="token punctuation">)</span> <span class="token punctuation">{</span>
    row<span class="token punctuation">.</span>clicks<span class="token operator">++</span><span class="token punctuation">;</span>
    <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token function">setState<span class="token punctuation">(</span></span><span class="token punctuation">{</span>
      rowData<span class="token punctuation">:</span> <span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>rowData<span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>

  <span class="token function">render<span class="token punctuation">(</span></span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    const rows <span class="token operator">=</span> <span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>rowData<span class="token punctuation">.</span><span class="token function">map<span class="token punctuation">(</span></span><span class="token punctuation">(</span>row<span class="token punctuation">,</span> ii<span class="token punctuation">)</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token punctuation">{</span>
      <span class="token keyword">return</span> &lt;Row key<span class="token operator">=</span><span class="token punctuation">{</span>ii<span class="token punctuation">}</span> data<span class="token operator">=</span><span class="token punctuation">{</span>row<span class="token punctuation">}</span> onClick<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>_onClick<span class="token punctuation">}</span><span class="token operator">/</span><span class="token operator">&gt;</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">return</span> <span class="token punctuation">(</span>
      &lt;PullToRefreshViewAndroid
        style<span class="token operator">=</span><span class="token punctuation">{</span>styles<span class="token punctuation">.</span>layout<span class="token punctuation">}</span>
        refreshing<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>isRefreshing<span class="token punctuation">}</span>
        onRefresh<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>_onRefresh<span class="token punctuation">}</span>
        colors<span class="token operator">=</span><span class="token punctuation">{</span><span class="token punctuation">[</span><span class="token string">'#ff0000'</span><span class="token punctuation">,</span> <span class="token string">'#00ff00'</span><span class="token punctuation">,</span> <span class="token string">'#0000ff'</span><span class="token punctuation">]</span><span class="token punctuation">}</span>
        progressBackgroundColor<span class="token operator">=</span><span class="token punctuation">{</span><span class="token string">'#ffff00'</span><span class="token punctuation">}</span>
        <span class="token operator">&gt;</span>
        &lt;ScrollView style<span class="token operator">=</span><span class="token punctuation">{</span>styles<span class="token punctuation">.</span>scrollview<span class="token punctuation">}</span><span class="token operator">&gt;</span>
          <span class="token punctuation">{</span>rows<span class="token punctuation">}</span>
        &lt;<span class="token operator">/</span>ScrollView<span class="token operator">&gt;</span>
      &lt;<span class="token operator">/</span>PullToRefreshViewAndroid<span class="token operator">&gt;</span>
    <span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>

  <span class="token function">_onRefresh<span class="token punctuation">(</span></span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token function">setState<span class="token punctuation">(</span></span><span class="token punctuation">{</span>isRefreshing<span class="token punctuation">:</span> <span class="token boolean">true</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token function">setTimeout<span class="token punctuation">(</span></span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token punctuation">{</span>
     <span class="token comment" spellcheck="true"> // prepend 10 items
</span>      const rowData <span class="token operator">=</span> Array<span class="token punctuation">.</span><span class="token function">from<span class="token punctuation">(</span></span><span class="token keyword">new</span> <span class="token class-name">Array</span><span class="token punctuation">(</span><span class="token number">10</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
      <span class="token punctuation">.</span><span class="token function">map<span class="token punctuation">(</span></span><span class="token punctuation">(</span>val<span class="token punctuation">,</span> i<span class="token punctuation">)</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token punctuation">(</span><span class="token punctuation">{</span>
        text<span class="token punctuation">:</span> <span class="token string">'Loaded row'</span> <span class="token operator">+</span> <span class="token punctuation">(</span><span class="token operator">+</span><span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>loaded <span class="token operator">+</span> i<span class="token punctuation">)</span><span class="token punctuation">,</span>
        clicks<span class="token punctuation">:</span> <span class="token number">0</span><span class="token punctuation">,</span>
      <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">)</span>
      <span class="token punctuation">.</span><span class="token function">concat<span class="token punctuation">(</span></span><span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>rowData<span class="token punctuation">)</span><span class="token punctuation">;</span>

      <span class="token keyword">this</span><span class="token punctuation">.</span><span class="token function">setState<span class="token punctuation">(</span></span><span class="token punctuation">{</span>
        loaded<span class="token punctuation">:</span> <span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>loaded <span class="token operator">+</span> <span class="token number">10</span><span class="token punctuation">,</span>
        isRefreshing<span class="token punctuation">:</span> <span class="token boolean">false</span><span class="token punctuation">,</span>
        rowData<span class="token punctuation">:</span> rowData<span class="token punctuation">,</span>
      <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span> <span class="token number">5000</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>

<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>


module<span class="token punctuation">.</span>exports <span class="token operator">=</span> PullToRefreshViewAndroidExample<span class="token punctuation">;</span></div></div><div class="docs-prevnext"><a class="docs-next" href="refreshcontrol.html#content">Next →</a></div>