
<h1>SMARTS - The unofficial Cheat Sheet</h1>

<table>
	<thead>
		<tr>
			<th>
				Structure
			</th>
			<th>
				SMARTS
			</th>
			<th>
				Comments
			</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>
				Carbonyl group. Low specificity
			</td>
			<td>
				[CX3]=[OX1]
			</td>
			<td>
				Hits carboxylic acid, ester, ketone, aldehyde, carbonic acid/ester,anhydride, carbamic acid/ester, acyl halide, amide.
			</td>
		</tr>
		<tr>
			<td>
				Carbonyl group
			</td>
			<td>
				[$([CX3]=[OX1]),$([CX3+]-[OX1-])]
			</td>
			<td>
				Hits either resonance structure
			</td>
		</tr>
		<tr>
			<td>
				Carbonyl with Nitrogen
			</td>
			<td>
				[OX1]=CN
			</td>
			<td>
				Hits amide, carbamic acid/ester, poly peptide
			</td>
		</tr>
		<tr>
			<td>
				Anhydride
			</td>
			<td>
				[CX3](=[OX1])[OX2][CX3](=[OX1])
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Amide
			</td>
			<td>
				[NX3][CX3](=[OX1])[#6]
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				
			</td>
			<td>
				
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Ether
			</td>
			<td>
				[OD2]([#6])[#6]
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				
			</td>
			<td>
				
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Primary or secondary amine, <strong>not amide</strong>
			</td>
			<td>
				[NX3;H2,H1;!$(NC=O)]
			</td>
			<td>
				Not ammonium ion (N must be 3-connected), not ammonia (H count can&#39;t be 3). Primary or secondary is specified by N&#39;s H-count (H2 &amp; H1 respectively). Also note that &quot;&amp;&quot; (and) is the dafault opperator and is higher precedence that &quot;,&quot; (or), which is higher precedence than &quot;;&quot; (and). Will hit cyanamides and thioamides
			</td>
		</tr>
		<tr>
			<td>
				
			</td>
			<td>
				
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Hydrazine
			</td>
			<td>
				[NX3][NX3]
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Azide
			</td>
			<td>
				[$(*-[NX2-]-[NX2+]#[NX1]),$(*-[NX2]=[NX2+]=[NX1-])]
			</td>
			<td>
				Hits any atom with an attached azide.
			</td>
		</tr>
		<tr>
			<td>
				Azo Nitrogen. Low specificity.
			</td>
			<td>
				[NX2]=N
			</td>
			<td>
				Hits diazene, azoxy and some diazo structures
			</td>
		</tr>
		<tr>
			<td>
				
			</td>
			<td>
				
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Nitrogen Heterocycle
			</td>
			<td>
				[$([nr5]:[nr5,or5,sr5]),$([nr5]:[cr5]:[nr5,or5,sr5])]
			</td>
			<td>
				5 member aromatic heterocycle w/ 2double bonds. contains N &amp; another non C (N,O,S) subclasses are furo-, thio-, pyrro- (replace CH o&#39; furfuran, thiophene, pyrrol w/ N)
			</td>
		</tr>
		<tr>
			<td>
				
			</td>
			<td>
				
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Substituted imine
			</td>
			<td>
				[CX3;$([C]([#6])[#6]),$([CH][#6])]=[NX2][#6]
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				s
			</td>
			<td>
				
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Nitrile
			</td>
			<td>
				[NX1]#[CX2]
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				<em>iso</em>Nitrile
			</td>
			<td>
				[NX1]#[CX2]
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				s
			</td>
			<td>
				
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Nitro group
			</td>
			<td>
				[$([NX3](=O)=O),$([NX3+](=O)[O-])][!#8]
			</td>
			<td>
				Hits both forms
			</td>
		</tr>
		<tr>
			<td>
				s
			</td>
			<td>
				
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Enol or Phenol
			</td>
			<td>
				[OX2H][$(C=C),$(cc)]
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				s
			</td>
			<td>
				
			</td>
			<td>
				
			</td>
		</tr>
		<tr>
			<td>
				Phosphoric acids
			</td>
			<td>
				[$(P(=[OX1])([$([OX2H]),$([OX1-]),$([OX2]P)])([$([OX2H]),$([OX1-]),$([OX2]P)])[$([OX2H]),$([OX1-]),$([OX2]P)]),$([P+]([OX1-])([$([OX2H]),$([OX1-]),$([OX2]P)])([$([OX2H]),$([OX1-]),$([OX2]P)])[$([OX2H]),$([OX1-]),$([OX2]P)])]
			</td>
			<td>
				Hits both depiction forms. Hits orthophosphoric acid and polyphosphoric acid anhydrides. Doesn&#39;t hit monophosphoric acid anhydride esters (including acidic mono- &amp; di- esters) but will hit some polyphosphoric acid anhydride esters (mono- esters on pyrophosphoric acid and longer, di- esters on linear triphosphoric acid and longer).
			</td>
		</tr>
		<tr>
			<td>
				Phosphoric esters
			</td>
			<td>
				$(P(=[OX1])([OX2][#6])([$([OX2H]),$([OX1-]),$([OX2][#6])])[$([OX2H]),$([OX1-]),$([OX2][#6]),$([OX2]P)]),$([P+]([OX1-])([OX2][#6])([$([OX2H]),$([OX1-]),$([OX2][#6])])[$([OX2H]),$([OX1-]),$([OX2][#6]),$([OX2]P)])]
			</td>
			<td>
				As above, but for esters
			</td>
		</tr>
	</tbody>
</table>

<p><a href="https://www.daylight.com/dayhtml_tutorials/languages/smarts/smarts_examples.html#CYCLE">https://www.daylight.com/dayhtml_tutorials/languages/smarts/smarts_examples.html#CYCLE</a></p>
~

