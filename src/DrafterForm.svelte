<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();

    let drafter = {
        name: '',
        height: 0,
        team: '',
        position: '',
        college_country: ''
    }

    let positions = [
        'PF',
        'C',
        'SG',
        'PG',
        'SF'
    ]

    let teams = [
        'Atlanta Hawks',
        'Boston Celtics',
        'Brooklyn Nets',
        'Charlotte Hornets',
        'Chicago Bulls',
        'Cleveland Cavaliers',
        'Dallas Mavericks',
        'Denver Nuggets',
        'Detroit Pistons',
        'Golden State Warriors',
        'Houston Rockets',
        'Indiana Pacers',
        'LA Clippers',
        'Los Angeles Lakers',
        'Memphis Grizzlies',
        'Miami Heat',
        'Milwaukee Bucks',
        'Minnesota Timberwolves',
        'New Orleans Pelicans',
        'New York Knicks',
        'Oklahoma City Thunder',
        'Orlando Magic',
        'Philadelphia 76ers',
        'Phoenix Suns',
        'Portland Trail Blazers',
        'Sacramento Kings',
        'San Antonio Spurs',
        'Toronto Raptors',
        'Utah Jazz',
        'Washington Wizards'
    ];

    function handleAddDrafter(event) {
        event.preventDefault();
        dispatch(
            'add_drafter',
            drafter
        );

        drafter = {
            name: '',
            height: 0,
            team: '',
            position: '',
            college_country: ''
        }
    };
</script>

<style></style>

<form on:submit={handleAddDrafter}>
    <div class="form-group">
        <label for="">Player Name</label>
        <input bind:value={drafter.name} type="text" class="form-control" placeholder="Jamal Crawford">
    </div>
    <div class="form-group">
        <label for="exampleInputPassword1">Height</label>
        <input bind:value={drafter.height} type="number" class="form-control">
    </div>
    <div class="form-group">
        <label for="">Team</label>
        <select bind:value={drafter.team} class="custom-select mr-sm-2" id="">
            <option selected>Choose...</option>
            {#each teams as team}
            <option value={team}>{team}</option>
            {/each}
        </select>
    </div>
        <div class="form-group">
        <label for="">Position</label>
        <select bind:value={drafter.position} class="custom-select mr-sm-2" id="">
            <option selected>Choose...</option>
            {#each positions as position}
            <option value={position}>{position}</option>
            {/each}
        </select>
    </div>
    <div class="form-group">
        <label for="">College/Country</label>
        <input bind:value={drafter.college_country} type="text" class="form-control" placeholder="Utah">
    </div>
    <button type="submit" class="btn btn-primary">Add</button>
</form>