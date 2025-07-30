<svelte:options customElement="copy-to-clipboard" />

<script>
    let {value, delay = 3000} = $props()
    let classname = $state('ready');
    function onclick() {
        navigator.clipboard.writeText(value);
        classname = 'copied';
        setTimeout(() => classname = 'ready', delay);
    }
</script>

<div>
    <button class="copy" type="button" onclick={onclick}>
        <span class={classname}></span>
    </button>
</div>

<style>
    div {
        position: absolute;
        right: 0.5rem;
        top: 0.5rem;
    }
    button {        
        position: relative;
        height: 1.5rem;
        width: 1.5rem;
        padding: 15%;
        display: flex;
        background: #f9f9f9;
        border: none;
        cursor: pointer;
        border-radius: 3px;
    }
    
    button:before {
        content: "Copy to clipboard";        
        position:absolute;
        
        /* vertically center */
        top:50%;
        transform:translateY(-50%);
        
        /* move to right */
        left:100%;
        margin-left:15px; /* and add a small left margin */
        
        /* basic styles */
        width:100px;
        padding:10px;
        border-radius:10px;
        background:#000;
        color: #fff;
        text-align:center;
        display: none;
        opacity:0;
        transition:0.5s opacity;
    }
    button:hover:before {
        display: block;
        opacity: 1;
    }
    button > span {        
        aspect-ratio: 1 / 1;		
        background-repeat: no-repeat;
        background-position: center;
        background-size: cover;
        transition: all 1s;
    }
    .ready {
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACoAAAAqCAYAAADFw8lbAAAAAXNSR0IArs4c6QAAAo1JREFUWEftmc2LT1EYxz8TYRbeoyEJCyHKblbKSs1sJGoWFohkISEvJSlbFsPCQlPYKDWEv0DMrGYjJC/lpbwkCguFKO637q3Tcc7vvNz7i3RPTU2/+5zv+dzvPeee8zy3h3ptCDgBLAcmZ0q9Ai4DJ4FvPo2eTHF1OwScrtHf7joGDBa6X1yauaALgefA1AZBJTUODLhgc0G3AKMW5KcAtKbGdCPmB/AT6LX6OWFzQbcDF40BRoDdAdD1wC0j5gawFbgObAjBNgV6BjiQAboJmAbcdMDeKX/7Lt1/AVQcPtijwKkQ6GxAf662uRIoL9ZxtNJ3wU4A/T7QlcB5YF3Cim4CVMMtKOb6W2Pcl8BSF+gi4AEwKwFSoTmgn4Fn1jiTgLUxoJeAbYmQuaAxw3gdfQSsMBReAB8dinOBJcbvMY6uAe7H0MU4KjATYD7wwSFuv0djQCVzAdiRAOt11AbVqtdcslsuqHT0NGZ6YGcAd3Mc7QZoJ0O1iM2t+K862oI2PUdbR1tHHXOgXfWVKbE7U2hTah1tHS0daLfQ0GIJXW8XU+XQOWBvyK6I6/OA902eR1XFu2IIqgr3MAIkFDKnyjrLQKVGq/S/XYCIPeEvA54Cyhq72ZS67KwDqr6qYBzuIqUOQ0oIX9cFlZsHgWMZdYBO9/cLuA3sAZ5UgbmP3hxI5cQ+YEqH0Y9b2eeRwq1rnnil538cLZsAjXn6w8Xg+41ApcwqdkS3/wZUtag30bftD1Shd1eTjqpAttoQ/NrpS0XCDdjlS5XWfXPUKWs/+rNFrWlfAkBOqG5e7+F3KZ1tUB0K7hU1osUpIomxKqErI0hqrtK49lt9P9rY4PtRXz8elx+9riYRlsG/Afy34CvacqJ5AAAAAElFTkSuQmCC);
    }
    .copied {
        background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAwCAYAAABXAvmHAAAAAXNSR0IArs4c6QAABfRJREFUaEPFmlfoXUUQh7/Y+4Mtxl6wi70ldhELvtgw1jd7Bwu+6IOKImqMNRYEMXbfFLtg772ALSp2McZgNxb0fGGv3Kyz55x7/+fqPN6zOzuzO/ub38zecXQjKwC7AtsA6wFrAssASwB/AT8BM4EPgXeA54BHga/Huvy4MSjQwEOBw4Eth9CjY88D04HbgNlD6GAYB1YGTgOOBBYbZtFgzo/AtcAlwJeD6BzEgQWrIz8OOC+FxiDrtB37M3ARcD7wW5tJbR1YF7gD2KSN0g7GvAxMrsLzgyZdbRzYH7hxhLtesvF74DDgnjonmhw4BrgSmL9pJ6rFZgAPAk8npPkY+CHNWwpYNSHU9sAe1eVdq4XOPwBtuKE0ts4BJ05rWMQFDK2rKqOebWFQ/5BJFbQen0KlboNEKwEjdKLkgGGjYXWKHwBOqqD0/QENz4d7vy4Hdq/R40btF4VT5IAKX6qJeZFCw4vHOqRD7vJlwKKF+d9VDmyRX+zcgYWAF2rQxsy5F/DKkEY2TTMh3leF5HKFgaLTtoAnMldyB84ELihM1vgdgXebrBjjdyPgyRonTgWmRA6slIxbPDDAsNlhhDufL+lJ6MQigS0i2zoVOn2Vn8DUio+cXNi9I0YQ800HdTRwTWHQxRVBPL3fAYnZJwVuI9oY9/+HPAzsFiwsdzKvzO7dgRMTlOVjvSwbdACVuV6TmYizKfBaOvmnAkOl5m8V4FxeNq3nwIsFSnxLSudd7v7mKb77maz1wvrAp8FCUu2Dgt9NnJN0YEKV6T4PEMk5E1Px0ZUDriVMS8lz8f6Z0HLZrgqj6HTM0ON14ODqVt8aTJTbrN2V5SlBPVbh/NYFnSbHK4Jv2igrXSP4dqAfjUUn53J14ipd+OA6blIUCur3UhrvRkIkopGolMsUFcsgIx5ySCr1unDgLOCcgiJDwbVur1nI0vXm4Pu9veOxCM9ls4QQJb2GwqXAxhXRegMQySKKcUCFZHcW7pi6z65Q5tyGXfLiSyNyeU8HZlWXZ+ng47LpW6R7ReDNbJ5IItXodyJCnH59Ioy76ynUidwo6mDM1IE5VQ0qictl4Zq6tFQrfJYuqYV5HeK4lmi0M/BLixjVll+DcXO6dqBn2J4VazSDlxCn39EW9lPrwDAhtHzKzpaKkdjEKlHiYYhhKYS+8QTE+6g+NX5frdkeK6S7KnSZr80WpjHGunnHam8QkZ3KFnKZoQMetUV2Ll6uKMH1j6uDx8hAx9tXGlTs/t0UTLp/rInM+bYGdbZJPC17PU2IE+m5LhX2+bepdVTC9C2VaFrQosNGraVeScRwIdb4H1S08SNgtWDiZD+OT/3IqMC39dGmXWJ3WlhcJVjki4RGJZrQ5JCOPx4McmMn9Ix28a2CQd6BNuHhVC/9E1Vvs78kjZJbk8H5d0PPbJ6LLfqJTQXNnxXSbDhAIW+BIiW2h/p6IokWLMPKRklPhHQn2FDrOWBJaSswKugfKqDUsEa1nadt3q2dggmerHdiVn/cS8xOKWg/Cri+7codjXOHo/pA9b4j+EYxT1+orq0iX/Ey2bH7L8RK0N2XQuRSbKs48IyqcrqwYKH0wN7QqBtb3jlRx7COxJ33BOZKDp2+wvhuZS0QiU7sXUjrXZyMO+97QMl4qbr55veSA/5u18tQWbJgkbTWu+KbVlfiRtpqt2EVhY3r+OBhc1fu9o+U2uv7JqJW115/JFVhPpuORYRKH1EitOnpFc4lj3fnC5UccJzI07TLKrZc9IHjmRa0o//kvU+WoRpWx2jNuBb0IQrWOdBzwu5Emycm+Yo5w6bs2ymviBiuYTiunppXGm4TIeI2+Qa7QcfWQXiTAyrcJ1HZ0p0YS/jUzTXmpdH/Cps2dyBXLCu1CCmhU9dOiDZS73kubLRImxPozVsgIYUtkFGdxsgeuvudt9tgb95LHnGnYU5DbiNg+Eo/9+GirQxyArlOk431rY/Rdh8G1dX7s4cdN/tD37Y1epg70KTbLsUuKUva47QRayfBv9so9j7N4iJVp3+3+RuolCgWkOfEQgAAAABJRU5ErkJggg==);
    }
</style>
