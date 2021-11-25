<script>
	let response = [
    {
        "target": "test-example.com",
        "safety": {
            "status": "UNKNOWN",
            "reputations": 40,
            "confidence": 28
        },
        "childSafety": {
            "reputations": 45,
            "confidence": 29
        },
        "categories": [
            {
                "id": 103,
                "name": "phishing",
                "confidence": 4
            },
            {
                "id": 104,
                "name": "scam",
                "confidence": 3
            }
        ]
    },
    {
        "target": "blacklist-example.co.tz",
        "safety": {
            "status": "NOT_SAFE",
            "reputations": 27,
            "confidence": 8
        },
        "childSafety": {},
        "categories": [
            {
                "id": 103,
                "name": "phishing",
                "confidence": 51
            }
        ],
        "blackList": [
            "phishing"
        ]
    },
    {
        "target": "adult-example.com",
        "safety": {
            "status": "SAFE",
            "reputations": 85,
            "confidence": 49
        },
        "childSafety": {
            "reputations": 9,
            "confidence": 50
        },
        "categories": [
            {
                "id": 401,
                "name": "adult content",
                "confidence": 96
            },
            {
                "id": 501,
                "name": "good site",
                "confidence": 51
            }
        ]
    }
]
</script>

<table>
	<tr>
		<th>Target</th>
		<th>Safety
			<table>
				<tr>
					<th>Status</th>
					<th>Reputations</th>
					<th>Confidence</th>
				</tr>
			</table>
		</th>
		<th>Child Safety<table>
				<tr>
					<th>Reputations</th>
					<th>Confidence</th>
				</tr>
			</table></th>
		<th>Categories</th>
	</tr>
		{#each response as respObj}
	<tr>
			<td>{respObj.target}</td>
			<td>
				<table>
					<tr>
						<td>{respObj.safety.status}</td>
						<td>{respObj.safety.reputations}</td>
						<td>{respObj.safety.confidence}</td>
					</tr>
				</table>
			</td>
		<td>
				<table>
					<tr>
						<td>{respObj.childSafety.reputations}</td>
						<td>{respObj.childSafety.confidence}</td>
					</tr>
				</table>
			</td>
		<td>
				<table>
					{#each respObj.categories as category}
						<tr>
						<th>Id:</th>
							<td>{category.id}</td>
					</tr>
					<tr>
						<th>Name:</th>
							<td>{category.name}</td>
					</tr>
					<tr>
						<th>Confidence:</th>
							<td>{category.confidence}</td>
					</tr>
					{/each}
			</table>
			</td>
		
	</tr>
		{/each}
</table>