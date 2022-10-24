# MultiLanguage
Multi Language 

Startup.cs Example...

    public void ConfigureServices(IServiceCollection services)
    { 
        ...
        services.AddLocalizer(connectionString);
        ...
    }
   
   
----------------------------------------------------------------------------------------------------------------------


Controller Example...

[ApiController]
[Route("[controller]")]
public class WeatherForecastController : ControllerBase
{
    private readonly ILocalizerResourceManager _resourceManager;

    private readonly DataContext _context;

    public WeatherForecastController(ILocalizerResourceManager resourceManager, DataContext context)
    {
        _resourceManager = resourceManager;
        _context = context;
    }

    [HttpGet]
    public string Get()
    {
        var data = _context.Set<Address>().Where(x => x.IsActive).ToList();

        var resourceValue = _resourceManager.GetResource("portal_global_ok");

        return "";
    }
}


----------------------------------------------------------------------------------------------------------------------

Suggestion...

- It is recommended to use the key names as the example below for cache etc. case.  ("portal_global_ok", "api_member_getmember_error")
( "portal name" _ "controller name" _ "method name" _ "button name" )
- All keys with the word global in their name can be used jointly.
  
