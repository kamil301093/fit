<script>

</script>

<template>
        <div>
                <form>
                        <label for="gender">gender:</label>
                        <select name="gender">
                                <option value="man">man</option>
                                <option value="man">woman</option>
                        </select>
                        <label for="weight">weight</label>
                        <input name="weight" type="text">
                        <label for="height">height</label>
                        <input name="height" type="text">
                        <label for="age">age</label>
                        <input name="age" type="text">
                        <input type="submit" value="Calculate">
                        <input type="button" value="Clear">
                </form>
                For women, BMR = 655.1 + (9.563 x weight in kg) + (1.850 x height in cm) - (4.676 x age in years)
                For men, BMR = 66.47 + (13.75 x weight in kg) + (5.003 x height in cm) - (6.755 x age in years)
        </div>
</template>