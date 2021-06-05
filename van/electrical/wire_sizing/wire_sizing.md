---
type: article
section: van
categories: 
 # one or more categories is permitted
 - electrical
navTitle: 
title: Wire Size
author: Nate
date: 2021-3-20
tags:
 - wirin
 - design
 - final
 - electrical
 - van

metatags:
 # nothing
cover: 
	# image file
	# img: img
	# if attribution is needed
	# source: [vecteezy]
	# url: url
---


The following evaluation assumes wire with insulation rated to 105C based on [this chart](http://assets.bluesea.com/files/resources/reference/21731.pdf) and voltage drop calculations based on [this calculator](https://www.calculator.net/voltage-drop-calculator.html?material=copper&wiresize=4.132&voltage=24&phase=dc&noofconductor=1&distance=6&distanceunit=feet&amperes=42&x=50&y=23).  [This chart](http://assets.bluesea.com/files/resources/newsletter/images/DC_wire_selection_chartlg.jpg) is also useful for quick reference.

It also assumes the BMS is using CAN to communicate/control discharge.  Based on this, it will provide 0A allowable discharge commands when the BMS cell low voltage protection of 2.9V (pack voltage of 23.2V) is reached.

# Main DC Distribution Wiring

## Battery to Positive Bus

Maximum theoritical/ideal charging current is 272A (Multiplus 24/3000 = 292A) .  Round trip wire length is approximately 3 ft.  Wire size is limited by ampacity, not voltage drop.  Minimum wire size is 0 AWG (00 AWG for Multiplus 23/3000).

* Battery at minimum 22.4V (BMS cell low cutoff of 2.8V)

* Max Aftermarket Alternator Charging = 150A

* Max Multiplus Compact Charging = 50A (Max Multiplus 23/3000 = 70A)

* 800W Primary Solar Charging (perfect efficiency) = 36A

* 800W Ground Array Solar Charging (perfect efficiency) = 36A

If the Multiplus 24/3000 is considered, maximum theoretical discharging current is 326A.  Round trip wire length is approximately 3 ft.  Wire size is limited by ampacity, not voltage drop.  Minimum wire size is 00 AWG.

* Battery at minimum 23.2V (BMS cell low voltage protection of 2.9v)
* No Aftermarket Alternator Charging
* No Solar
* No Shore Power
* Max Multiplus 24/3000 Discharge = 284A (see below)
* Max DC Load Discharge = 42A (see below)

## Aftermarket Alternator to Positive Bus

Maximum charge current is 150A.  Round trip wire length is approximately 44 ft.  By ampacity, minimum wire size is 4 AWG.  By voltage drop, minimum wire size is 0 AWG.

## Multiplus Compact Inverter/Charger to Positive Bus

Maximum charge current is 50A.  Maximum discharge current is 184A assuming minimum battery voltage (23.2V), peak power (4000W), and maximum efficiency (94%).  Round trip wire length is approximately 11.5 ft.  Wire size is limited by ampacity, not voltage drop. Minimum wire size is 2 AWG.

Note: This is extremely conservative.  The 4000W rating is a [2 minute overload capability](https://community.victronenergy.com/questions/21511/overload-duration-on-multiplus.html).  While this case will be acommodated in the cabling (and fusing), for things like busbar sizing, continuous rates will be used (i.e., 150A busbars will be considered with the multiplus connection adjacent to the battery connection).

## Multiplus 24/3000 Inverter/Charger to Positive Bus [Alternate]

Maximum charge current is 70A, and thus not limiting.

Maximum discharge current is 275A assuming minimum battery voltage (23.2V), peak power (6000W), and maximum efficiency (94%).  Round trip wire length is approximately 11.5 ft.  Wire size is limited by ampacity, not voltage drop.  Minimum wire size is 0 AWG.

Maximum discharge current is 138A assuming minimum battery voltage (23.2V), rated power (3000W), and maximum efficiency (94%).  Round trip wire length is approximately 11.5 ft.  Wire size is limited by voltage drop. Minimum wire size is 6 AWG.

Note: This is extremely conservative.  The 6000W rating is a [2 minute overload capability](https://community.victronenergy.com/questions/21511/overload-duration-on-multiplus.html).  While this case will be acommodated in the cabling (and fusing), for things like busbar sizing, continuous rates will be used (i.e., 150A busbars will be considered with the multiplus connection adjacent to the battery connection).



## Solar MPPT to Positive Bus

For future flexibility, a ground array up to 800W is assumed.  This will use a second MPPT that will be paralleled with the primary roof array of 800W at a terminal, and then routed to the Positive Bus.  Wiring from the point of parallel to the Positive Bus and the branch to the MPPTs will be sized for the same ampacity to allow use of a single fuse in the Positive Bus to cover wire including the branches.

Maximum charge current is 72A assuming minimum battery voltage (22.4V) and perfect MPPT efficiency.  Round trip wire length is approximately 11.5 ft.  Wire size is limited by ampacity, not voltage drop.  Minimum wire size is 8 AWG.  To simplify wire ordering and termination, 2 AWG will be considered.

## Main DC Panel to Positive Bus

Maximum discharge current is 42A based on the maximum load (944W) in the converter sizing study in [this spreadsheet](https://docs.google.com/spreadsheets/d/1X7njD1I48CtzVDgUu9Sp_Ce2chWM4oQiqM1aEl7uJWI/edit?usp=sharing) assuming minimum battery voltage (23.2V).  Round trip wire length is approximately 12 ft.  By ampacity, minimum wire size is 12 AWG.  By voltage drop, minimum wire size is 11 AWG.  However, as this distribution panel functions as the source to downstream loads, voltage drop to the panel should be minimized.  To minimize voltage drop, and simplify wire ordering and termination, 2 AWG will be considered.

## Chassis Ground to Positive Bus

All current sourced from the Aftermarket Alternator, 150A, will flow through this connection.  Its required size is bounded by that calculation.  To simplify wire ordering and termination, the same wire size will be used.

# Branch DC Wiring
