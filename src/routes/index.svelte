<script context="module">
export async function load({ fetch }){
        const res = await fetch('https://www.boredapi.com/api/activity')
        const activity = await res.json()

        if(res.ok){
            return{
                status : res.status,
                props : {
                    activity 
                }
            }
        }

        return{
            status : res.status,
            error : new Error('Could not fetch any activity')
          
        }
    }


</script>

<script>
    export let activity
</script>

<header>
    <h2>Acticity suggestion if you are getting bored</h2>
    <h3>Refresh page for new activity</h3>
</header>
<div class="activity">
<table> 
    <tr><td>Activity</td><td>{activity.activity}</td></tr>
    <tr><td >Type</td><td class="title">{activity.type}</td></tr>
    <tr><td>Participants</td><td>{activity.participants}</td></tr>
    <tr><td>Price</td><td>{activity.price}</td></tr>
    <tr><td>Link</td><td>{activity.link}</td></tr>
    <tr><td>Accesibility</td><td>{activity.accessibility}</td></tr>    
</table>



  
  
</div>




<style>
    .title{
        text-transform: capitalize;
    }
    header{
      text-align: center;
    }
    .activity {
  display: flex;
  justify-content: center;
  align-items: center;  
}
    
   
    table { 
	width: 750px; 
	border-collapse: collapse; 
	margin:50px auto;
	}

/* Zebra striping */
tr:nth-of-type(odd) { 
	background: #eee; 
	}

th { 
	background: #3498db; 
	color: white; 
	font-weight: bold; 
	}

td, th { 
	padding: 10px; 
	border: 1px solid #ccc; 
	text-align: left; 
	font-size: 18px;
	}

/* 
Max width before this PARTICULAR table gets nasty
This query will take effect for any screen smaller than 760px
and also iPads specifically.
*/
@media 
only screen and (max-width: 760px),
(min-device-width: 768px) and (max-device-width: 1024px)  {

	table { 
	  	width: 100%; 
	}

	/* Force table to not be like tables anymore */
	table, thead, tbody, th, td, tr { 
		display: block; 
	}
	
	/* Hide table headers (but not display: none;, for accessibility) */
	thead tr { 
		position: absolute;
		top: -9999px;
		left: -9999px;
	}
	
	tr { border: 1px solid #ccc; }
	
	td { 
		/* Behave  like a "row" */
		border: none;
		border-bottom: 1px solid #eee; 
		position: relative;
		padding-left: 50%; 
	}

	td:before { 
		/* Now like a table header */
		position: absolute;
		/* Top/left values mimic padding */
		top: 6px;
		left: 6px;
		width: 45%; 
		padding-right: 10px; 
		white-space: nowrap;
		/* Label the data */
		content: attr(data-column);

		color: #000;
		font-weight: bold;
	}

}

</style>