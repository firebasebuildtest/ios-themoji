puts "Running fastlane"

require 'snapshot'
options = {}
Snapshot.config = FastlaneCore::Configuration.create(Snapshot::Options.available_options, options)
Snapshot::Runner.new.work

puts 'running screen_grid'
screen_grid.run

puts "Running fastlane to generate and upload an ipa file..."

options = {
  xcodebuild: {
    scheme: "Themoji"
  }
}

require 'fastlane'
result = Fastlane::OneOff.run(action: "build_and_upload_to_appetize",
                          parameters: options)

device_grid.run(
  public_key: result,
  languages: ["en", "de"],
  devices: ["iphone5s", "iphone6splus", "ipadair"]
)