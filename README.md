# 摘要算法

## 什么是单向散列函数

> 称输入为**消息**，输出为**散列值**，经过单向散列函数，单向散列函数就是根据输入的**消息**，输出根据消息计算出来的散列值。

单向散列函数的性质：

1. 根据任意长度的消息计算出固定长度的散列值
2. 能够快速计算出散列值
3. 消息不同散列值不同
4. 具备单向性

> * 为了能够确认完整性，消息中哪怕只有1 比特的改变，也会有**很高的概率**产生不同的散列值
> * 两个不同的消息产生同一个散列值的情况成为碰撞。难以发现碰撞的性质成为抗碰撞性
> * 弱抗碰撞性：要找到和该条消息具有相同散列值的另外一条消息是非常困难的
> * 强碰撞性：要找到两条具有相同散列值的消息是非常困难的
> * 密码技术中使用的单向散列函数都是要求具备弱抗碰撞性以及强抗碰撞性的
> * 单向性是指：无法通过散列值反算出消息的性质

---

## 单向散列函数的实际应用

1. 检测软件是否被篡改
2. 基于口令的加密
3. 消息验证码
4. 数字签名
5. 伪随机数生成器
6. 一次性口令

---

## 主要的几种单向散列函数
<table class="wikitable" style="margin-top: 0px; width:100%">
<caption>SHA函数对比</caption>
<tbody><tr style="vertical-align:bottom;">
<th colspan="2">算法和变体</th>
<th>输出散列值长度

（bits）</th>
<th>中继散列值长度

（bits）</th>
<th>数据区块长度

（bits）</th>
<th>最大输入消息长度

（bits）</th>
<th>循环次数</th>
<th>使用到的运算符</th>
<th>碰撞攻击

（bits）</th>
<th>性能示例<sup id="cite_ref-3" class="reference">[[3]](#cite_note-3)</sup>

([MiB](/wiki/Mebibyte "Mebibyte")/s)</th>
</tr>
<tr style="text-align:center;vertical-align:top;">
<td colspan="2">**[MD5](/wiki/MD5 "MD5")**（作为参考）</td>
<td>128</td>
<td>128

<span class="nowrap" style="white-space:nowrap;">(4 × 32)</span></td>
<td>512</td>
<td>无限<sup id="cite_ref-4" class="reference">[[4]](#cite_note-4)</sup></td>
<td>64</td>
<td>And, Xor, Rot, <span class="nowrap" style="white-space:nowrap;">Add (mod&nbsp;2<sup>32</sup>),</span> Or</td>
<td style="background: #faa; color: black; vertical-align: middle; text-align: center;" class="no table-no">&lt;64

（发现碰撞）</td>
<td>335</td>
</tr>
<tr style="text-align:center;vertical-align:top;">
<td colspan="2">**<span class="nowrap" style="white-space:nowrap;">[SHA-0](/wiki/SHA-0 "SHA-0")</span>**</td>
<td>160</td>
<td>160

<span class="nowrap" style="white-space:nowrap;">(5 × 32)</span></td>
<td>512</td>
<td>2<sup>64</sup> − 1</td>
<td>80</td>
<td rowspan="2">And, Xor, Rot, <span class="nowrap" style="white-space:nowrap;">Add (mod&nbsp;2<sup>32</sup>),</span> Or</td>
<td style="background: #faa; color: black; vertical-align: middle; text-align: center;" class="no table-no">&lt;80

（发现碰撞）</td>
<td>-</td>
</tr>
<tr style="text-align:center;vertical-align:top;">
<td colspan="2">**<span class="nowrap" style="white-space:nowrap;">[SHA-1](/wiki/SHA-1 "SHA-1")</span>**</td>
<td>160</td>
<td>160

<span class="nowrap" style="white-space:nowrap;">(5 × 32)</span></td>
<td>512</td>
<td>2<sup>64</sup> − 1</td>
<td>80</td>
<td style="background: #faa; color: black; vertical-align: middle; text-align: center;" class="no table-no">&lt;80<sup id="cite_ref-5" class="reference">[[5]](#cite_note-5)</sup>

（发现碰撞<sup id="cite_ref-6" class="reference">[[6]](#cite_note-6)</sup>）</td>
<td>192</td>
</tr>
<tr style="text-align:center;vertical-align:top;">
<td rowspan="2">**<span class="nowrap" style="white-space:nowrap;">[SHA-2](/wiki/SHA-2 "SHA-2")</span>**</td>
<td>_SHA-224_

_SHA-256_</td>
<td>224

256</td>
<td>256

<span class="nowrap" style="white-space:nowrap;">(8 × 32)</span></td>
<td>512</td>
<td>2<sup>64</sup> − 1</td>
<td>64</td>
<td>And, Xor, Rot, <span class="nowrap" style="white-space:nowrap;">Add (mod&nbsp;2<sup>32</sup>),</span> Or, Shr</td>
<td style="background: #99FF99; color: black; vertical-align: middle; text-align: center;" class="yes table-yes2">112

128</td>
<td>139</td>
</tr>
<tr style="text-align:center;vertical-align:top;">
<td>_SHA-384_

_SHA-512_

_<span class="nowrap" style="white-space:nowrap;">SHA-512/224</span>_

_<span class="nowrap" style="white-space:nowrap;">SHA-512/256</span>_</td>
<td>384

512

224

256</td>
<td>512

<span class="nowrap" style="white-space:nowrap;">(8 × 64)</span></td>
<td>1024</td>
<td>2<sup>128</sup> − 1</td>
<td>80</td>
<td>And, Xor, Rot, <span class="nowrap" style="white-space:nowrap;">Add (mod&nbsp;2<sup>64</sup>),</span> Or, Shr</td>
<td style="background: #99FF99; color: black; vertical-align: middle; text-align: center;" class="yes table-yes2">192

256

112

128</td>
<td>154</td>
</tr>
<tr style="text-align:center;vertical-align:top;">
<td rowspan="2">**<span class="nowrap" style="white-space:nowrap;">[SHA-3](/wiki/SHA-3 "SHA-3")</span>**</td>
<td>_SHA3-224_

_SHA3-256_

_SHA3-384_

_SHA3-512_</td>
<td>224

256

384

512</td>
<td rowspan="2">1600

<span class="nowrap" style="white-space:nowrap;">(5 × 5 × 64)</span></td>
<td>1152

1088

832

576</td>
<td rowspan="2">无限<sup id="cite_ref-7" class="reference">[[7]](#cite_note-7)</sup></td>
<td rowspan="2">24<sup id="cite_ref-8" class="reference">[[8]](#cite_note-8)</sup></td>
<td rowspan="2">And, Xor, Rot, Not</td>
<td style="background: #99FF99; color: black; vertical-align: middle; text-align: center;" class="yes table-yes2">112

128

192

256</td>
<td>-</td>
</tr>
<tr style="text-align:center;vertical-align:top;">
<td>_SHAKE128_

_SHAKE256_</td>
<td><span class="nowrap" style="white-space:nowrap;">_d_ (arbitrary)</span>

<span class="nowrap" style="white-space:nowrap;">_d_ (arbitrary)</span></td>
<td>1344

1088</td>
<td style="background: #99FF99; color: black; vertical-align: middle; text-align: center;" class="yes table-yes2">min(_d_/2, 128)

min(_d_/2, 256)</td>
<td>-</td>
</tr>
</tbody></table>


---

## Keccak

---

## 对于单向散列函数的攻击

---

## 单向散列函数不能解决的问题

---

## 消息认证码

---

## 消息认证码的应用实例

---

## 消息认证码的实现方法

---

## HMAC

---

## 对消息认证码的攻击

---

## 消息认证码不能解决的问题

---



