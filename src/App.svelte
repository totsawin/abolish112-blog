<script>
	import { Temporal } from 'proposal-temporal/lib/index.mjs';
	const todayDate = Temporal.now.plainDateISO();
	const people = [
	 {
		  name: `Jatupat 'Pai Dao Din' Boonpatraksa`,
		  nickname: 'pai',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 3, day: 8 }),
		  releasedDate: Temporal.PlainDate.from({ year: 2021, month: 4, day: 23 }),
	  },
	  {
		  name: `Parit 'Penguin' Chiwarak`,
		  nickname: 'penguin',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 2, day: 9 }),
		  releasedDate: Temporal.PlainDate.from({ year: 2021, month: 5, day: 11 }),
	  },
	  {
		  name: `Panupong 'Mike' Jadnok`,
		  nickname: 'mike',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 3, day: 8 }),
	  },
	  {
		  name: `Somyot Pruksakasemsuk`,
		  nickname: 'somyot',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 2, day: 9 }),
		  releasedDate: Temporal.PlainDate.from({ year: 2021, month: 4, day: 23 }),
	  },
	  {
		  name: `Arnon Nampa`,
		  nickname: 'arnon',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 2, day: 9 }),
	  },
	  {
		  name: `Patiwat Saraiyaem, 'Mor Lam Bank'`,
		  nickname: 'bank',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 2, day: 9 }),
		  releasedDate: Temporal.PlainDate.from({ year: 2021, month: 4, day: 9 }),
	  },
	  {
		  name: `Panusaya Sithijirawattanakul`,
		  nickname: 'rung',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 3, day: 8 }),
		  releasedDate: Temporal.PlainDate.from({ year: 2021, month: 5, day: 6 }),
	  },
	  {
		  name: `Chaiamorn 'Ammy' Kaewwiboonpan`,
		  nickname: 'ammy',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 3, day: 4 }),
		  releasedDate: Temporal.PlainDate.from({ year: 2021, month: 5, day: 11 }),
	  },
	  {
		  name: `Parinya Cheewin Kulpathom aka 'Port Faiyen'`,
		  nickname: 'port',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 3, day: 6 }),
		  releasedDate: Temporal.PlainDate.from({ year: 2021, month: 5, day: 12 }),
	  },
	  {
		  name: `Piyarat 'Toto' Jongthep`,
		  nickname: 'toto',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 3, day: 6 }),
		  releasedDate: Temporal.PlainDate.from({ year: 2021, month: 5, day: 5 }),
	  },
	  {
		  name: `Promsorn 'Fah' Veerathamjaree`,
		  nickname: 'fah',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 3, day: 17 }),
		  releasedDate: Temporal.PlainDate.from({ year: 2021, month: 5, day: 10 }),
	  },
	  {
		  name: `Chookiat 'Justin' Saengwong`,
		  nickname: 'justin',
		  detainedDate: Temporal.PlainDate.from({ year: 2021, month: 3, day: 23 }),
	  }
  ]

  function getNumberOfDaysUnderDetained(detainedDate, releasedDate = todayDate) {
	return detainedDate.until(releasedDate, { largestUnit: 'days' }).days;
  }
</script>
<main class="people">
	{#each people as person}
		<div class="individual">
			<div class="individual__name">
				{ person.name }
			</div>
			<div class="individual__caption">      
				<span>{getNumberOfDaysUnderDetained(person.detainedDate, person.releasedDate)} Days Held Under Pre-Trial Detention</span>
			</div>
			<div class="individual__image">
				<img src="./assets/{person.nickname}.jpg" alt="{person.name}"/>
				{#if person.releasedDate}
					<div class="stamp is-bailed">Bailed</div>
				{/if}	
			</div>
  		</div>
	{/each}	  
</main>

<style>
	:global(body) {
		/* this will apply to <body> */
		background-color: black;
		margin: 0;
	}

	.people {
		display: grid;
		grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
		column-gap: 10px;
		row-gap: 20px;
  	}

	.individual {
		position: relative;
		width: 100%;
		margin: 0 auto;
		background-color: #4a4a4a;
		color: #fff;
		box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
		display: grid;
		font-family: "helvetica", "arial", sans-serif;
		grid-template-rows: 10% 5% auto;
  	}
	.individual__name {
		align-items: center;
		display: grid;
		font-size: 1.5em;
		font-weight: bold;
		padding-left: 1rem;
		border-bottom: 1px solid;
	}

	.individual__caption {
		/* background-color: #ddb0e1; */
		color: #f9f2e2;
		align-items: center;
		display: grid;
		font-size: 1em;
		padding-left: 1rem;
		border-bottom: 1px solid;
	}

	.individual__image {
		position: relative;
		background-color: #98d6f7;
		overflow: hidden;
	}

	img {
		width: 100%;
		height: 100%;
	}

	.stamp {
		font-weight: 700;
		text-transform: uppercase;
		mix-blend-mode: multiply;
		position: absolute;
		top: 50%;
		transform: translate(-50%, -50%);
	}

	.is-bailed {
		color: #C4C4C4;
		border: 1rem double #C4C4C4;
		transform: rotate(-5deg);
		font-size: 6rem;
		font-family: "Open sans", Helvetica, Arial, sans-serif;
		border-radius: 0;
		padding: 0.5rem;
	}
</style>