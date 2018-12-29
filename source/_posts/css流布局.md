---
title: css流布局
tags:
  - css
---
css可以利用 ==collumn-count== 属性实现瀑布流流布局
例子代码如下：
```
<html>
<head>
	<meta charset="UTF-8">
	<title>瀑布流测试</title>
	<style>
		.water-fall{
			width: 1200px;
			height: auto;
			margin: 0 auto;
			column-count: 4;
			-webkit-column-count:4;

		}
		.water-fall .item{	
			box-sizing: border-box;
			border: #ccc 1px solid;
			padding: 5px;
			margin-top: 10px;
		}
		.water-fall .item:nth-child(4n+1){
			background-color: #4e0f0f;
		}
		.water-fall .item:nth-child(4n+2){
			background-color: #2cc468;
		}
		.water-fall .item:nth-child(4n+3){
			background-color: #c49c2c;
		}
		.water-fall .item:nth-child(4n){
			background-color: #c42cbf;
		}
	</style>
</head>
<body>
	<div class="water-fall">
		<div class="item">Lorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sitLorem ipsum dolor sit.</div>
		<div class="item">Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum,Iste quas nostrum, corrupti.</div>
		<div class="item">Voluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, doloreVoluptas dolor, dolore minima!</div>
		<div class="item">Amet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciuntAmet, et nesciunt recusandae!</div>
		<div class="item">Assumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimusAssumenda vitae omnis possimus.</div>
		<div class="item">Voluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optioVoluptas quis dolores optio?</div>
		<div class="item">Voluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniamVoluptatibus esse beatae veniam.</div>
		<div class="item">Nihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibusNihil tempora beatae voluptatibus.</div>
		<div class="item">Eveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquamEveniet adipisci, quisquam sed.</div>
		<div class="item">Totam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobisTotam eaque quos nobis.</div>
		<div class="item">Praesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cumPraesentium vero corrupti cum?</div>
		<div class="item">Error odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt temporeError odio sunt tempore.</div>
	</div>
</body>
</html>
```
只要在外面的div的属性里加上一个属性：collumn-count、-webkit-collumn-count，然后置顶一个值，是这一列显示的列数。