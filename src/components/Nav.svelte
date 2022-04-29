<script>
	import Logo from '../assets/Logo.svg';
</script>

<nav>
	<a href="/">SvelteFlix</a>
	<a href="https://www.nadernasr.ca">
    <img src={Logo} alt="back to creator home" />
  </a>
</nav>

<style>
	nav {
		display: flex;
		min-height: 10vh;
		align-items: flex-start;
		justify-content: space-around;
	}

	a {
		font-size: 3rem;
		font-weight: 700;
		font-family: 'Poppins';
		text-decoration: none;
		padding: 10px;
	}

  img {
    width: 70px;
  }
</style>
